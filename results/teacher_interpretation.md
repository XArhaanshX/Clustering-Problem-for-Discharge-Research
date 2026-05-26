# Interpretation and Observations

### Teacher-Ready Interpretation & Conclusion

**1. Did SVM improve Void classification?**
Marginally. In BGST (50dB), Void improved from ~47% to ~57%, but remained extremely poor under 20dB noise (~44%). In CST, SVM actually performed *worse* than the simple Rule-Based approach for Void classification. 

**2. Did SVM improve Surface classification?**
Yes, primarily in CST (improving 20dB Surface classification from ~66% to ~81%). In BGST and HST, Surface was already handled excellently by the Rule-Based classifier (~97-98%), and SVM performed identically or slightly worse.

**3. Did CNN improve Void classification?**
Partially, but only under ideal conditions. The CNN reached ~70% for Void on BGST reference data, which is an improvement over the Rule-Based approach (~47%), but it still plummeted to ~56% when 20 dB noise was introduced.

**4. Did CNN improve Surface classification?**
No. In almost all scenarios, the CNN traded off Surface accuracy to marginally boost Void accuracy. For example, in BGST 50dB, CNN dropped Surface accuracy down to ~77% compared to the Rule-Based classifier's ~97%.

**5. Did either approach reach ~90% for Void and Surface simultaneously?**
**NO.** None of the models were able to push both Void and Surface to ~90%. An optional Phase 2 test using an enhanced 8-feature benchmark was also run, but it also failed to reach ~90% for Void, indicating a hard mathematical feature overlap ceiling regardless of the algorithm used.

**6. Which method performed best?**
The **Rule-Based Classifier** remains the most balanced and interpretable approach. While SVM and CNN can occasionally squeeze 10-15% more accuracy out of a specific class (like Void in reference conditions), they do so via complex non-linear boundaries that trade off performance in other areas (like Surface). 

**7. Under which condition?**
All models uniformly collapsed under the **20 dB noisy condition**, particularly in HST data where the Sharp Point class completely drops to near 0% across Rule-Based, SVM, and CNN paradigms. Advanced models do not solve feature-smearing caused by heavy 20 dB noise.
