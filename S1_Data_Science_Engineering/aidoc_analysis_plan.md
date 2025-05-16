# Aidoc Pulmonary Embolism Analysis Plan

## 1. Project Overview

This document outlines the statistical analysis plan for evaluating the Aidoc AI tool for pulmonary embolism (PE) detection. The analysis addresses both clinical and operational questions to provide insights into the AI system's performance.

**Research Questions:**
1. What is the detection rate of pulmonary embolism (PE) and incidental pulmonary embolism (iPE) by the Aidoc AI system?
2. How does the Aidoc AI system perform in detecting right heart strain (RHS) through RV/LV ratio measurement?
3. How does the real-world performance of the Aidoc AI system compare with the results reported in literature?

## 2. Data Sources

- **Primary Data Source**: Aidoc AI output CSV file (`algorithms_report_2025-03-13_2025-04-23_115623.csv`)
- **Data Structure**: The CSV contains accession numbers, module types (PE, IPE, RV/LV), and AI results
- **Time Period**: March 13, 2025 to April 23, 2025
- **Data Limitations**: Missing RV/LV values before April 15, 2025

## 3. Methodology

### 3.1 Data Preprocessing

1. **Data Cleaning**:
   - Handle quotation marks in string fields
   - Convert "true"/"false" strings to boolean values
   - Convert numeric strings to appropriate numeric types

2. **Data Structuring**:
   - Flatten the data to have one row per imaging study with all AI results
   - Parse date/time information for temporal analysis

### 3.2 Statistical Analysis Plan

#### 3.2.1 Basic Statistics
- Count and percentage of positive PE detections
- Count and percentage of positive iPE detections
- Count of cases with RV/LV ratio > 1.0 (RHS)
- Count of cases with RV/LV ratio > 1.5 (significant RHS)

#### 3.2.2 Performance Metrics
For both PE and iPE modules, calculate:
- Sensitivity (Recall)
- Specificity
- Precision (Positive Predictive Value)
- Accuracy
- F1 Score
- Negative Predictive Value

#### 3.2.3 Comparative Analysis
- Compare monthly performance metrics with literature values
- Statistical tests to determine if differences are significant

### 3.3 Visualization Plan

1. **Confusion Matrices**:
   - Confusion matrices for PE and iPE from literature
   - Confusion matrices for PE and iPE from monthly data (if ground truth available)

2. **Metrics Comparison**:
   - Bar charts comparing monthly metrics with literature values

3. **RV/LV Analysis**:
   - Histogram of RV/LV ratios for positive PE/iPE cases
   - Highlighted thresholds at 1.0 and 1.5 for RHS detection

4. **Temporal Analysis**:
   - Line graphs showing monthly trends of positive PE and iPE cases
   - Overlay with total scan volume

## 4. Implementation Details

### 4.1 Code Structure

The implementation follows a modular design with the following components:

1. **Data Processing Functions**:
   - `preprocess_data()`: Clean and structure the data
   - `flatten_per_image()`: Aggregate results by accession number

2. **Analysis Functions**:
   - `count_positive_PEs_total()`: Count positive PE cases
   - `count_positive_iPEs()`: Count positive iPE cases
   - `count_RVLV_above_val()`: Count cases with RV/LV above threshold
   - `calculate_metrics_from_confusion()`: Calculate performance metrics

3. **Visualization Functions**:
   - `create_confusion_matrix_plot()`: Generate confusion matrix visualization
   - `create_metrics_comparison_plot()`: Compare monthly and literature metrics
   - `create_RVLV_histogram()`: Analyze RV/LV ratio distribution
   - `create_monthly_trend_plot()`: Show temporal trends

4. **Reporting Function**:
   - `generate_pdf_report()`: Create comprehensive PDF report

### 4.2 Libraries Used

- **pandas**: Data manipulation and analysis
- **numpy**: Numerical operations
- **matplotlib**: Basic plotting
- **seaborn**: Enhanced visualizations
- **fpdf**: PDF report generation

## 5. Outputs and Deliverables

The main deliverable is a comprehensive PDF report with the following sections:

1. **Basic Statistics**: Overview of monthly data
2. **Confusion Matrices**: From literature and monthly data
3. **Performance Comparison**: Monthly vs. literature
4. **Visualizations**: RV/LV distribution and monthly trends
5. **Patient List**: Cases with RHS (RV/LV > 1.0)
6. **Conclusion**: Summary of findings and recommendations

## 6. Future Enhancements

1. **Ground Truth Integration**:
   - Incorporate radiologist-verified results for accuracy assessment
   - Calculate true performance metrics (currently using literature as benchmark)

2. **Advanced Analysis**:
   - Subgroup analysis by patient demographics
   - Analysis of false positives/negatives to identify patterns

3. **Operational Insights**:
   - Workflow impact analysis
   - Time-to-diagnosis measurements

4. **Interactive Dashboard**:
   - Develop an interactive dashboard for ongoing monitoring
   - Alert system for performance degradation

## 7. Ethical Considerations

- Patient data privacy and confidentiality maintained
- Analysis focused on AI system performance, not individual patient outcomes
- Results contextualized to avoid over-reliance on AI without clinical verification

## 8. Conclusion

This statistical analysis plan provides a robust framework for evaluating the Aidoc AI tool for pulmonary embolism detection. The implementation will generate valuable insights for clinical teams and inform future AI deployment decisions within the NHS.
