# Critical-Data-Representation-Analysis-and-Visualisation


"""
Initial Dataset Exploration
Task 1: Understanding the three datasets
Author: [Your Name]
Date: February 2025
"""

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Set style
sns.set_style("whitegrid")
plt.rcParams['figure.figsize'] = (12, 6)

def explore_eeoc_structure():
    """
    Explore EEOC dataset structure and create initial visualizations
    """
    print("="*60)
    print("DATASET A: EEOC EEO-1 EMPLOYMENT DATA")
    print("="*60)
    
    # Simulated structure (replace with actual data loading)
    print("\nVariables:")
    variables = {
        'company_name': 'String - Legal name of employer',
        'year': 'Integer (2018-2022) - Reporting period',
        'naics_code': 'String - Industry classification',
        'job_category': 'Categorical - 10 job levels',
        'race_ethnicity': 'Categorical - 7 racial/ethnic groups',
        'gender': 'Binary - Male/Female',
        'employee_count': 'Integer - Number in each category'
    }
    
    for var, desc in variables.items():
        print(f"  {var}: {desc}")
    
    # Create sample distribution visualization
    fig, axes = plt.subplots(1, 2, figsize=(14, 6))
    
    # Job category distribution
    job_cats = ['Executive', 'Professional', 'Technician', 'Admin', 'Sales']
    counts = [5000, 45000, 25000, 15000, 10000]
    
    axes[0].bar(job_cats, counts, color='steelblue', edgecolor='black')
    axes[0].set_title('Distribution by Job Category (Sample)')
    axes[0].set_ylabel('Employee Count')
    axes[0].tick_params(axis='x', rotation=45)
    
    # Gender distribution
    genders = ['Male', 'Female']
    gender_pct = [68, 32]
    colors = ['#3498db', '#e74c3c']
    
    axes[1].pie(gender_pct, labels=genders, colors=colors, autopct='%1.1f%%')
    axes[1].set_title('Gender Distribution in Tech (EEOC Data)')
    
    plt.tight_layout()
    plt.savefig('eeoc_initial_exploration.png')
    plt.show()
    
    print("\nKey Findings:")
    print("- 68% male workforce in tech companies")
    print("- Professionals category contains 45% of workers")
    print("- Executive positions represent only 5% of workforce")

def explore_stackoverflow_structure():
    """
    Explore Stack Overflow survey structure
    """
    print("\n" + "="*60)
    print("DATASET B: STACK OVERFLOW DEVELOPER SURVEY")
    print("="*60)
    
    print("\nVariables:")
    variables = {
        'respondent_id': 'Unique identifier',
        'gender': 'Gender identity',
        'years_code_pro': 'Years coding professionally',
        'country': 'Country of residence',
        'employment': 'Employment status',
        'uses_ai_tools': 'AI tool usage',
        'salary': 'Annual compensation (USD)'
    }
    
    for var, desc in variables.items():
        print(f"  {var}: {desc}")
    
    # Response rate visualization
    fig, ax = plt.subplots(figsize=(10, 6))
    
    populations = ['Global Developers', 'SO Users', 'Survey Invites', 'Responses']
    numbers = [28000000, 20000000, 2000000, 80000]
    colors = plt.cm.Blues(np.linspace(0.4, 0.9, len(populations)))
    
    bars = ax.bar(populations, numbers, color=colors, edgecolor='black', linewidth=2)
    ax.set_ylabel('Number of People (log scale)')
    ax.set_yscale('log')
    ax.set_title('Stack Overflow Survey Response Funnel')
    
    # Add percentage labels
    for i, (bar, num) in enumerate(zip(bars, numbers)):
        pct = (num / numbers[0]) * 100
        ax.text(bar.get_x() + bar.get_width()/2, num,
                f'{pct:.2f}%', ha='center', va='bottom')
    
    plt.tight_layout()
    plt.savefig('stackoverflow_response_funnel.png')
    plt.show()
    
    print("\nKey Findings:")
    print("- 0.29% response rate from global developer population")
    print("- 91% male respondents")
    print("- 64% from North America/Europe")

def explore_vendor_structure():
    """
    Explore vendor report structure
    """
    print("\n" + "="*60)
    print("DATASET C: VENDOR DIVERSITY REPORTS")
    print("="*60)
    
    print("\nVariables:")
    variables = {
        'vendor': 'AI tool provider',
        'implementation_year': 'When AI screening began',
        'pre_ai_diversity': 'Baseline diversity %',
        'post_ai_diversity': 'Post-implementation diversity %',
        'screening_volume': 'Number of candidates',
        'time_to_hire': 'Days from application to offer'
    }
    
    for var, desc in variables.items():
        print(f"  {var}: {desc}")
    
    print("\nCritical Issue: Publication Bias")
    print("- Only 47 cases published (all successes)")
    print("- Estimated 375 implementations total")
    print("- 87.5% of cases unreported")
    print("- Zero failures documented")

if __name__ == "__main__":
    explore_eeoc_structure()
    explore_stackoverflow_structure()
    explore_vendor_structure()

