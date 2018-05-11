# LinkedIn Resume Parser

This library parses LinkedIn PDF resumes from Recruiter portal into a set of PHP entities. The entities are based on the various sections
found in each resume, making it easy to extract information such as current / previous roles, education history,
certifications etc.

## Basic Use

```php
$resumeParser = new \LinkedInResumeParser\Parser();
$parsedResume = $resumeParser->parse('/path/to/resume.pdf');

echo $parsedResume->getFullName();
// Ross Kinsman

echo $parsedResume->getCurrentRole()->getOrganisation();
// The Drum

echo $parsedResume->getCurrentRole()->getStart()->format('F, Y');
// August, 2016

foreach ($parsedResume->getSkills() as $skill) {
    echo $skill;
    // PHP
    // Git
    // ...
}

foreach ($parsedResume->getEducationEntries() as $educationEntry) {
    echo $educationEntry->getInstitution();
    // University of Strathclyde
}
```
