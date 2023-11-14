# Data about K-12 teacher years of experience in California

In 2023, CalMatters published the series “[The Turnover Trap](https://calmatters.org/series/teacher-turnover/)” examining the push to keep more veteran teachers in the schools where students struggle most. To get a sense of the issue around the state, CalMatters used the California Public Records Act to request records from over three dozen school districts for data on teacher experience and turnover per school. Our survey of schools included the largest districts as well as a variety of urban, suburban and rural communities in order to get a diverse perspective on a statewide issue. In a months-long analysis process, reporters cleaned and combined the requested records with school-level data from the state on student poverty and demographics to look for trends with teacher tenures.

## Methodology

We began requesting this data during the summer of 2022. The school information, FRPM – students on Free or Reduced-Price Meals, a proxy for student poverty – and enrollment is from the California Dept. of Education (CDE). Specifically, the 2021-22 [“FRPM – Student Poverty Data” dataset](https://www.cde.ca.gov/ds/ad/filessp.asp) was used as it was the most recent available at the time of analysis. The “Enrollment (K-12)” and “Percent (%) Eligible FRPM (K-12)” values were used for enrollment and FRPM here. The CDE district and school codes are unique and persist across academic years.

Each district provided data in a different format, so CalMatters cleaned and standardized each dataset in the following ways:
* We only included teachers assigned to K-12 schools. Pre-K child care centers were excluded, nor principals, psychologists, counselors, etc.
* We asked for total years of service as of 9/1/2022 if possible. If only a district-specific hire or seniority date was provided, we calculated experience years as of 9/1/2022. The type of information provided is indicated in the `teacher_exp_districts.csv` file.
* We used total years of teaching experience as defined by the district when available. However, some districts only provided in-district experience, and others did not clarify which type was provided. The type is indicated in the `teacher_exp_districts.csv` file.

### Special cases
* Oakland Unified provided teacher experience years in five-year brackets, so separate calculations may be needed to analyze these schools.
* San Juan Unified did not specify exact years for one teacher, using “20+” instead.


### Other notes
* A few schools opened after the 2021-22 school year and thus did not have 2021-22 FRPM data.
* Some districts may have the same teacher assigned to multiple school sites. So summing the number of teachers per school may not be equivalent to total unique teachers in a district.
* Some but not all districts included charter schools within their jurisdiction.

## Data files

### teacher_exp_districts.csv
Each row is a school district.

<table>
<thead>
<tr>
<th>Column name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
  <td>district_name</td>
  <td><p>Name of the school district.</p></td>
</tr>
<tr>
  <td>district_code</td>
  <td><p>Unique five-digit code corresponding to the district. Can be matched across CDE datasets.</p></td>
</tr>
<tr>
  <td>county</td>
  <td><p>County where the district is located.</p></td>
</tr>
<tr>
  <td>type_of_years</td>
  <td><ul>
    <li><b>total</b>: The years refer to total years of teaching experience (according to the district).</li>
    <li><b>district</b>: The years refer to years of teaching experience at this district.</li>
    <li><b>unclear</b>: The type of experience years could not be determined.</li>
  </ul></td>
</tr>
<tr>
  <td>calculated_years</td>
  <td><ul>
    <li><b>included</b>: The district provided the years.</li>
    <li><b>calculated</b>: The years were calculated from the hire or seniority date provided by the district to 9/1/2022.</li>
  </ul></td>
</tr>
<tr>
  <td>schools_included</td>
  <td><p>The number of schools with teacher experience data in the dataset.</p></td>
</tr>
</tbody>
</table>

### teacher_exp_schools.csv
Each row is a school.

<table>
<thead>
<tr>
<th>Column name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
  <td>district_name</td>
  <td><p>Name of the school district.</p></td>
</tr>
<tr>
  <td>district_code</td>
  <td><p>Unique five-digit code corresponding to the district. Can be matched across CDE datasets.</p></td>
</tr>
<tr>
  <td>school_name</td>
  <td><p>Name of the school, according to CDE.</p></td>
</tr>
<tr>
  <td>school_code</td>
  <td><p>Unique seven-digit code corresponding to the school. Can be matched across CDE datasets.</p></td>
</tr>
<tr>
  <td>school_type</td>
  <td><p>Type of the school, according to CDE.</p></td>
</tr>
<tr>
  <td>teachers_included</td>
  <td><p>Number of teachers included in the dataset for the school.</p></td>
</tr>
<tr>
  <td>enrollment_k12_2122</td>
  <td><p>Enrollment (K-12), according to the 2021-22 CDE FRPM – Student Poverty Data dataset. If blank, the school opened in 2022 so did not have a field in the CDE dataset.</p></td>
</tr>
<tr>
  <td>frpm_k12_2122</td>
  <td><p>Percent (%) Eligible FRPM (K-12), according to the 2021-22 CDE FRPM – Student Poverty Data dataset. If blank, the school opened in 2022 so did not have a field in the CDE dataset.</p></td>
</tr>
</tbody>
</table>

### teacher_exp_teachers.csv
Each row is a teacher.

<table>
<thead>
<tr>
<th>Column name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
  <td>district_name</td>
  <td><p>Name of the school district.</p></td>
</tr>
<tr>
  <td>district_code</td>
  <td><p>Unique five-digit code corresponding to the district. Can be matched across CDE datasets.</p></td>
</tr>
<tr>
  <td>school_name</td>
  <td><p>Name of the school, according to CDE.</p></td>
</tr>
<tr>
  <td>school_code</td>
  <td><p>Unique seven-digit code corresponding to the school. Can be matched across CDE datasets.</p></td>
</tr>
<tr>
  <td>hire_or_experience_date</td>
  <td><p>Included if the district provided hire or seniority dates instead of raw experience years.</p></td>
</tr>
<tr>
  <td>experience_years</td>
  <td><p>Either calculated or provided experience years for the teacher.</p></td>
</tr>
</tbody>
</table>

## Data use

If you use this dataset, please mention it was collected, combined and cleaned by CalMatters. We would love to know how you used it. If you have any questions about this dataset, feel free to contact us.

[CalMatters](https://calmatters.org/) is a nonpartisan, nonprofit journalism venture committed to explaining how California’s state Capitol works and why it matters.