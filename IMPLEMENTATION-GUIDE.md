# SENSEA Survey Implementation Guide

## Quick Start

This guide provides step-by-step instructions for implementing the SENSEA 2025 Feedback Survey on various platforms.

## Platform-Specific Guides

### Google Forms

1. **Create New Form**
   - Go to forms.google.com
   - Create new form titled "SENSEA 2025 Feedback Survey"
   - Add description from markdown file

2. **Add Sections**
   For each of the 7 main sections (8 with demographics):
   - Click "Add section" 
   - Copy section title
   - Add questions from corresponding section

3. **Question Configuration**
   
   **Multiple Choice Questions:**
   - Select "Multiple choice" type
   - Enter question text
   - Add all options
   - Toggle "Required" for mandatory questions

   **Rating Scale Questions:**
   - Select "Linear scale" type
   - Set 1 to 10 scale
   - Add scale labels (min/max descriptions)
   - Mark as required

   **Multiple Select Questions:**
   - Select "Checkboxes" type
   - Enter all options
   - Add "Other" option where indicated
   - Set as optional unless specified

   **Open-Ended Questions:**
   - Select "Paragraph" type
   - Leave as optional (most open-ended questions are)

4. **Settings**
   - Enable "Show progress bar"
   - Enable "Shuffle question order" (optional)
   - Set "Limit to 1 response" if needed
   - Configure email collection if required

### SurveyMonkey

1. **Create Survey**
   - Click "Create Survey"
   - Choose "Start from scratch"
   - Name: "SENSEA 2025 Feedback Survey"

2. **Import Questions**
   - Use JSON structure for reference
   - Create pages for each section
   - Add page titles matching section headers

3. **Question Types**
   - Multiple choice → "Multiple Choice (One Answer)"
   - Rating scale → "Matrix/Rating Scale" or "Slider"
   - Multiple select → "Multiple Choice (Multiple Answers)"
   - Open-ended → "Comment Box" or "Single Textbox"

4. **Logic and Branching**
   - Consider skip logic based on "N/A" responses
   - Branch off-peak questions based on satisfaction
   - Optional: Branch membership questions based on interest level

5. **Design**
   - Choose professional theme
   - Add SENSEA branding/logo
   - Ensure mobile preview looks good

### Typeform

1. **Start New Typeform**
   - Create new typeform
   - Select "Start from scratch"

2. **Welcome Screen**
   - Add welcome message
   - Brief survey description
   - Estimated completion time (8-12 minutes)

3. **Add Questions**
   - Use "Multiple choice" for single-select
   - Use "Picture choice" for visual options
   - Use "Opinion scale" for rating questions
   - Use "Long text" for open-ended

4. **Features to Enable**
   - Progress bar
   - Question numbers
   - Logic jumps where appropriate
   - Thank you screen with contact info

5. **Design**
   - Choose calming spa-themed colors
   - Add SENSEA branding
   - Select readable font

### Custom Web Implementation

#### Frontend Structure

```html
<!-- Example structure for one section -->
<section id="pricing-review" class="survey-section">
  <h2>1. Spa Day Pass Pricing Review</h2>
  
  <div class="question" data-required="true">
    <label for="q1-1">
      1.1 How would you rate the current pricing for our Spa Day Pass?
    </label>
    <div class="options">
      <input type="radio" name="q1-1" value="very-fair" id="q1-1-1">
      <label for="q1-1-1">Very Fair</label>
      
      <input type="radio" name="q1-1" value="fair" id="q1-1-2">
      <label for="q1-1-2">Fair</label>
      
      <input type="radio" name="q1-1" value="slightly-high" id="q1-1-3">
      <label for="q1-1-3">Slightly High</label>
      
      <input type="radio" name="q1-1" value="too-high" id="q1-1-4">
      <label for="q1-1-4">Too High</label>
    </div>
  </div>
  
  <div class="question" data-required="true">
    <label for="q1-2">
      1.2 On a scale of 1-10, how likely are you to purchase a Spa Day Pass?
    </label>
    <input type="range" name="q1-2" id="q1-2" min="1" max="10" 
           class="rating-scale" data-show-value="true">
    <div class="scale-labels">
      <span>Not likely at all</span>
      <span>Very likely</span>
    </div>
  </div>
</section>
```

#### JavaScript Validation

```javascript
// Validation function
function validateSection(sectionId) {
  const section = document.getElementById(sectionId);
  const requiredQuestions = section.querySelectorAll('[data-required="true"]');
  
  let isValid = true;
  
  requiredQuestions.forEach(question => {
    const inputs = question.querySelectorAll('input, textarea, select');
    const hasValue = Array.from(inputs).some(input => {
      if (input.type === 'radio' || input.type === 'checkbox') {
        return input.checked;
      }
      return input.value.trim() !== '';
    });
    
    if (!hasValue) {
      question.classList.add('error');
      isValid = false;
    } else {
      question.classList.remove('error');
    }
  });
  
  return isValid;
}

// Progress tracking
function updateProgress() {
  const totalSections = 7;
  const completedSections = document.querySelectorAll('.section-completed').length;
  const progress = (completedSections / totalSections) * 100;
  
  document.getElementById('progress-bar').style.width = `${progress}%`;
  document.getElementById('progress-text').textContent = 
    `${completedSections} of ${totalSections} sections completed`;
}
```

#### CSS Styling

```css
/* Mobile-first responsive design */
.survey-section {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

.question {
  margin-bottom: 30px;
  padding: 20px;
  background: #f9f9f9;
  border-radius: 8px;
}

.question.error {
  border: 2px solid #d32f2f;
  background: #ffebee;
}

.options {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-top: 15px;
}

/* Rating scale */
.rating-scale {
  width: 100%;
  margin: 15px 0;
}

.scale-labels {
  display: flex;
  justify-content: space-between;
  font-size: 0.9em;
  color: #666;
}

/* Mobile optimization */
@media (max-width: 768px) {
  .survey-section {
    padding: 15px;
  }
  
  .question {
    padding: 15px;
  }
  
  input[type="radio"],
  input[type="checkbox"] {
    min-width: 20px;
    min-height: 20px;
  }
}

/* Progress bar */
.progress-container {
  position: sticky;
  top: 0;
  background: white;
  padding: 15px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  z-index: 100;
}

.progress-bar {
  height: 8px;
  background: #4caf50;
  border-radius: 4px;
  transition: width 0.3s ease;
}
```

## Mobile Optimization Checklist

- [ ] Large tap targets (minimum 44x44px)
- [ ] Readable font sizes (minimum 16px)
- [ ] Adequate spacing between options
- [ ] Responsive layout that adapts to screen size
- [ ] No horizontal scrolling required
- [ ] Progress indicator visible
- [ ] Save and continue later option
- [ ] Fast loading times

## Accessibility Checklist

- [ ] All form inputs have associated labels
- [ ] Color is not the only indicator of state
- [ ] Sufficient color contrast (WCAG AA minimum)
- [ ] Keyboard navigation works throughout
- [ ] Screen reader compatible
- [ ] Error messages are clear and specific
- [ ] Instructions are provided where needed
- [ ] Skip navigation available

## Data Collection Best Practices

### Before Launch

1. **Test Thoroughly**
   - Test on multiple devices
   - Test with different browsers
   - Test with screen readers
   - Test skip logic and branching

2. **Pilot Test**
   - Send to small group (5-10 people)
   - Collect feedback on clarity
   - Check completion time
   - Identify confusing questions

3. **Review Data Storage**
   - Ensure GDPR compliance
   - Configure data retention
   - Set up secure storage
   - Plan data backup

### During Collection

1. **Monitor Responses**
   - Check completion rates
   - Identify drop-off points
   - Monitor for technical issues
   - Track response quality

2. **Communication**
   - Send reminders if needed
   - Provide support contact
   - Thank respondents
   - Update on timeline

### After Collection

1. **Data Cleaning**
   - Remove duplicate responses
   - Check for invalid data
   - Handle incomplete responses
   - Standardize open-ended responses

2. **Analysis**
   - Calculate key metrics
   - Identify trends
   - Segment by demographics
   - Generate visualizations

## Distribution Strategies

### Email Campaign
- Subject: "Help Shape SENSEA's Future - 5 Minutes Survey"
- Personalized greeting
- Clear call-to-action
- Incentive if applicable (e.g., entry to win spa treatment)
- Mobile-friendly email design

### In-Spa Distribution
- QR codes at reception
- Tablets available for immediate completion
- Staff mention during checkout
- Printed cards with URL

### Social Media
- Instagram Stories with poll teasers
- Facebook post with survey link
- LinkedIn for B2B feedback
- Hashtag campaign: #SENSEAFeedback2025

### Website Integration
- Pop-up after 30 seconds (exit intent)
- Banner on homepage
- Post-booking thank you page
- Member portal notification

## Response Incentives

Consider offering:
- Entry to win free spa day pass
- 10% discount on next visit
- Loyalty points bonus
- Exclusive preview of new services
- Early access to membership program

## Timeline Recommendation

- **Week 1**: Launch and initial promotion
- **Week 2-3**: Send reminders to non-responders
- **Week 4**: Final reminder and close survey
- **Week 5**: Data analysis and reporting
- **Week 6**: Share insights with team and plan actions

## Support Resources

For technical issues or questions:
- Email: feedback@sensea.com
- Survey helpdesk: Available during business hours
- FAQ page: Common questions about the survey
- Contact form: For detailed inquiries

## Success Metrics

Track these KPIs:
- **Response rate**: Target 30-40% of customer base
- **Completion rate**: Target 80%+ completion
- **Average time**: Should be 8-12 minutes
- **Mobile vs Desktop**: Monitor split
- **Drop-off points**: Identify problematic sections

## Next Steps After Survey

1. **Analyze Results**
   - Compile key findings
   - Create executive summary
   - Generate detailed reports

2. **Share Insights**
   - Present to management
   - Share with staff
   - Communicate to customers (summary)

3. **Take Action**
   - Prioritize improvements
   - Implement changes
   - Track impact

4. **Follow-Up**
   - Thank participants
   - Share what changed based on feedback
   - Build trust for future surveys

---

*Last Updated: December 2025*
