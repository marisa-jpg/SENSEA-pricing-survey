# SENSEA 2025 Feedback Survey

This repository contains the comprehensive survey structure for SENSEA's 2025 Feedback Initiative, designed to collect customer feedback across various aspects of the spa's services and offerings.

## Overview

The survey is structured to gather insights on:
- Spa Day Pass Pricing
- Membership Offerings
- Social and Ritual Events
- Opening Hours (with focus on off-peak times)
- Loyalty Program preferences
- Treatments and Additional Services
- Overall satisfaction and areas for improvement

## Survey Files

### 1. `SENSEA-2025-Feedback-Survey.md`
A human-readable markdown version of the survey, suitable for:
- Quick review and editing
- Documentation purposes
- Converting to various survey platforms
- Sharing with stakeholders

### 2. `survey-structure.json`
A structured JSON format containing:
- Complete survey schema
- Question types and validation rules
- Section organization
- Metadata and accessibility settings

This format is ready for integration with:
- Survey platforms (Google Forms, SurveyMonkey, Typeform)
- Custom web applications
- Mobile survey apps
- Data analysis tools

## Survey Structure

### Core Sections

1. **Spa Day Pass Pricing Review**
   - Price perception questions
   - Willingness to pay assessments
   - Open feedback on pricing

2. **New Membership Offering Test**
   - Interest levels in membership programs
   - Preferred membership types
   - Expected benefits
   - Price sensitivity analysis

3. **Social and Ritual Events**
   - Past attendance tracking
   - Event satisfaction ratings
   - Future event preferences
   - Frequency expectations

4. **Spa Opening Hours Review (Off-Peak)**
   - Current hours satisfaction
   - Off-peak pricing interest
   - Preferred off-peak time slots
   - Discount motivation thresholds

5. **Loyalty Program**
   - Importance assessment
   - Preferred rewards
   - Tracking preferences
   - Recommendation likelihood with loyalty program

6. **Treatments and Additional Offerings**
   - Current treatment experience
   - Quality ratings
   - Desired new treatments
   - Service variety satisfaction

7. **Areas for Improvement, Final Thoughts**
   - Improvement priorities
   - Overall experience ratings
   - Net Promoter Score (NPS)
   - Open feedback sections

8. **Demographics (Optional)**
   - Age range
   - Visit frequency
   - Discovery channel

## Question Types

The survey uses a variety of question types for comprehensive data collection:

### Multiple Choice
Single-select questions for clear preference indication
- Example: "How would you rate the current pricing?" (Very Fair, Fair, Slightly High, Too High)

### Rating Scales
1-10 scales for nuanced feedback
- Example: "On a scale of 1-10, how likely are you to purchase..."

### Multiple Select
Allow respondents to choose multiple applicable options
- Example: "What benefits would you expect from a membership?" (select all that apply)

### Open-Ended
Free-text responses for detailed feedback
- Example: "What are your thoughts on our current Spa Day Pass pricing?"

## Design Best Practices

The survey follows established survey design principles:

### User Experience
- **Clear Headers**: Each section has a descriptive title
- **Logical Flow**: Questions progress from general to specific
- **Consistent Formatting**: Uniform question structure throughout
- **Mobile Optimization**: Questions designed for easy mobile completion
- **Accessibility**: Screen reader compatible, keyboard navigable

### Data Quality
- **Balanced Options**: Multiple-choice options cover the full range
- **Mix of Required/Optional**: Core questions required, detailed feedback optional
- **Avoid Leading Questions**: Neutral phrasing throughout
- **Open-Ended Balance**: Strategic placement of open questions to reduce survey fatigue

### Response Optimization
- **Question Variety**: Mix of question types maintains engagement
- **Optional Sections**: Demographics optional to reduce abandonment
- **Progress Indication**: Clear section markers show completion progress
- **Estimated Time**: Approximately 8-12 minutes to complete

## Implementation Guidelines

### For Digital Platforms

1. **Google Forms**
   - Use markdown file as reference
   - Create sections matching the structure
   - Enable progress bar
   - Set required questions as indicated

2. **SurveyMonkey / Typeform**
   - Import JSON structure where supported
   - Configure question logic and branching
   - Enable mobile optimization
   - Set up data export formats

3. **Custom Implementation**
   - Use JSON schema for database design
   - Implement validation rules per question type
   - Add progress tracking
   - Ensure responsive design

### For Print Distribution

- Use markdown version as template
- Include clear instructions
- Provide adequate space for written responses
- Add contact information for questions

## Data Analysis Recommendations

### Key Metrics to Track

1. **Pricing Insights**
   - Price perception distribution
   - Ideal price point consensus
   - Willingness to pay trends

2. **Membership Viability**
   - Interest level percentages
   - Preferred membership types
   - Target price ranges

3. **Operational Optimization**
   - Off-peak interest rates
   - Optimal discount thresholds
   - Preferred time slots

4. **Customer Satisfaction**
   - Net Promoter Score (NPS)
   - Overall satisfaction ratings
   - Service quality assessments

5. **Feature Priorities**
   - Most requested treatments
   - Top loyalty program features
   - Event preferences

## Contact

For questions or feedback about this survey structure:
- Email: feedback@sensea.com
- Project Repository: [SENSEA-pricing-survey](https://github.com/marisa-jpg/SENSEA-pricing-survey)

## Version History

- **v1.0** (2025) - Initial survey structure for 2025 Feedback Initiative
  - 7 core sections
  - 40+ questions
  - Multiple question types
  - Mobile-optimized design
  - Accessibility features

## License

This survey structure is proprietary to SENSEA and intended for internal use and authorized research purposes.
