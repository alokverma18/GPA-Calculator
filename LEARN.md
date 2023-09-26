# GPA Calculator Tutorial

## Introduction

Welcome to the tutorial! Here, you will walk through the process of creating a GPA calculator web application using Streamlit.

## Prerequisites

- Python

- Streamlit module

Run this commmand on your Terminal to install Streamlit

```bash
  
pip install streamlit
  
```


## Python Script


### Import the modules
```python
 
import streamlit as st
 
```

## Grade -> Point Conversion
```python
 
def grade_to_points(grade):
    grade_map = {
        'O': 10.0, 'A+': 9.0, 'A': 8.0, 'B+': 7.0, 'B': 6.0, 'C': 5.5, 'F':0.0
    }
    return grade_map.get(grade.upper(), 0.0)
 
```
## GPA Calculation
```python
 
def calculate_gpa(credits, grades):
    total_credits = 0
    weighted_sum = 0
    
    for credit, grade in zip(credits, grades):
        credit = int(credit)
        points = grade_to_points(grade)
        
        total_credits += credit
        weighted_sum += credit * points
    
    if total_credits == 0:
        return 0.0
    
    gpa = weighted_sum / total_credits
    return gpa

 
```

## Web Interface

#### Title
```python
 
st.set_page_config(page_title="GPA Calculator", page_icon=":mortar_board:")

st.title("GPA Calculator")
 
```

#### Inputs

```python
 
num_courses = st.number_input("Enter the number of Courses:", min_value=1, step=1, value=1)

credits = []
grades = []

st.write("Enter Credits and select Grade for each Course:")


columns = st.columns(2)
for i in range(num_courses):
    
    with columns[0]:  # Column for Credits
        credit = st.number_input(f"Credits:", min_value=0, step=1, value=0, key=f"credit_{i}")
        credits.append(credit)
    
    with columns[1]:  # Column for Grades
        grade = st.selectbox(f"Grade:", ('O', 'A+', 'A', 'B+', 'B', 'C', 'F'), index=0, key=f"grade_{i}")
        grades.append(grade)
 
```

#### Calculate button
```python
 
if st.button("Calculate GPA"):
    gpa = calculate_gpa(credits, grades)    
    st.subheader(f"Your GPA is {gpa:.2f}")

```

#### Footer

```python
 
col = st.columns(4)

with col[3]:
    st.write("Made with ❤ by [Alok](https://github.com/alokverma18/gpa-calculator)")
 
```

## Test Application
```bash
  
streamlit run gpa.py
  
```
This should open this GPA Calculator in your Web Browser

## Hosting Streamlit App

Streamlit Sharing is a free platform provided by Streamlit that allows you to easily host and share your Streamlit apps with the world. Follow these steps to get your Streamlit app up and running on Streamlit Sharing:
 
1. Create a GitHub Repository and upload your Python file.

2. Sign Up for [Streamlit Sharing](https://share.streamlit.io/)

3. Connect your GitHub Account (if not done already)

4. Click the "New App" button on the Streamlit Sharing dashboard.

5. Follow the prompts to connect your GitHub repository to Streamlit Sharing.

6. Configure the settings for your app, including the branch to deploy, the command to run your app, etc (if required).
   
7. Provide your Custom URL

8. Click the "Deploy" button.

9. Wait for the deployment process to complete. Streamlit Sharing will build and host your app.

10. Once the deployment is successful, you will receive a unique URL for your hosted Streamlit app.

For more information, refer to [Streamlit Community Cloud](https://docs.streamlit.io/streamlit-community-cloud)

### That's it! You have successfully hosted your Streamlit web app.
## 
## Thanks
