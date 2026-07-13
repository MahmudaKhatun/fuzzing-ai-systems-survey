---
layout: default
title: Technique-to-Study Mapping
---

# Technique-to-Study Mapping

[← Back to Home]({{ site.baseurl }}/)

[← Extended Technique-Family Analysis]({{ site.baseurl }}/results/technique-families.html)

This page provides the complete study-level mapping for the normalized
technique families used in RQ2 of the survey
*Fuzzing AI Systems: Foundations, Techniques, and Open Challenges*.

The analysis includes **125 primary studies** identified within the
**January 2015–February 2026 search window**. Technique-family labels are
**not mutually exclusive** because many studies combine multiple central
fuzzing mechanisms.

Each paper ID is linked to its corresponding entry on the
[Primary Studies page]({{ site.baseurl }}/results/primary-studies.html),
where the full title, authors, year, venue, and DOI or publisher URL are
provided.

## Detailed Mapping

<div style="overflow-x:auto;">

<table style="min-width:1000px;">
<thead>
<tr>
<th style="min-width:190px;">Normalized technique family</th>
<th style="text-align:center; min-width:90px;"># Studies</th>
<th>Primary-study IDs</th>
</tr>
</thead>

<tbody>

<tr>
<td><strong>Mutation-based</strong></td>
<td style="text-align:center;">63</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p004">P004</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p005">P005</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p006">P006</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p007">P007</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p008">P008</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p009">P009</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p010">P010</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p011">P011</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p014">P014</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p016">P016</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p018">P018</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p021">P021</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p024">P024</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p026">P026</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p031">P031</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p032">P032</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p034">P034</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p035">P035</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p038">P038</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p043">P043</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p044">P044</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p051">P051</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p058">P058</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p060">P060</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p061">P061</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p066">P066</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p068">P068</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p069">P069</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p076">P076</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p088">P088</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p089">P089</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p103">P103</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p106">P106</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p116">P116</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p125">P125</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p130">P130</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p133">P133</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p136">P136</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p137">P137</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p144">P144</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p145">P145</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p146">P146</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p148">P148</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p152">P152</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p154">P154</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p160">P160</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p164">P164</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p167">P167</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p169">P169</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p170">P170</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p172">P172</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p174">P174</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p176">P176</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p178">P178</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p180">P180</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p182">P182</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p193">P193</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p197">P197</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p198">P198</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p200">P200</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p201">P201</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p204">P204</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p208">P208</a></td>
</tr>
<tr>
<td><strong>Coverage-guided</strong></td>
<td style="text-align:center;">52</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p004">P004</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p007">P007</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p012">P012</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p019">P019</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p024">P024</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p025">P025</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p027">P027</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p028">P028</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p029">P029</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p031">P031</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p032">P032</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p033">P033</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p039">P039</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p040">P040</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p042">P042</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p045">P045</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p046">P046</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p061">P061</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p066">P066</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p080">P080</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p086">P086</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p096">P096</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p104">P104</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p120">P120</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p121">P121</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p125">P125</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p130">P130</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p133">P133</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p140">P140</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p142">P142</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p143">P143</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p144">P144</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p145">P145</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p146">P146</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p148">P148</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p153">P153</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p154">P154</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p157">P157</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p158">P158</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p162">P162</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p165">P165</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p167">P167</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p174">P174</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p176">P176</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p178">P178</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p180">P180</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p182">P182</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p197">P197</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p200">P200</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p201">P201</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p202">P202</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p204">P204</a></td>
</tr>
<tr>
<td><strong>Learning-based</strong></td>
<td style="text-align:center;">30</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p002">P002</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p012">P012</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p013">P013</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p015">P015</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p023">P023</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p026">P026</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p030">P030</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p035">P035</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p068">P068</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p078">P078</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p079">P079</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p081">P081</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p082">P082</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p090">P090</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p099">P099</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p101">P101</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p103">P103</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p104">P104</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p114">P114</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p122">P122</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p125">P125</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p127">P127</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p130">P130</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p133">P133</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p136">P136</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p143">P143</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p145">P145</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p146">P146</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p147">P147</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p152">P152</a></td>
</tr>
<tr>
<td><strong>Constraint-guided</strong></td>
<td style="text-align:center;">17</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p001">P001</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p003">P003</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p005">P005</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p006">P006</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p008">P008</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p011">P011</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p017">P017</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p020">P020</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p076">P076</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p077">P077</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p100">P100</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p111">P111</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p113">P113</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p114">P114</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p147">P147</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p172">P172</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p198">P198</a></td>
</tr>
<tr>
<td><strong>Search/Heuristic-guided</strong></td>
<td style="text-align:center;">16</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p018">P018</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p020">P020</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p022">P022</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p029">P029</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p030">P030</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p035">P035</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p038">P038</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p044">P044</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p045">P045</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p058">P058</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p069">P069</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p083">P083</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p087">P087</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p145">P145</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p152">P152</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p193">P193</a></td>
</tr>
<tr>
<td><strong>Differential testing</strong></td>
<td style="text-align:center;">15</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p001">P001</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p003">P003</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p008">P008</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p009">P009</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p010">P010</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p015">P015</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p016">P016</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p018">P018</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p091">P091</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p095">P095</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p119">P119</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p156">P156</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p170">P170</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p193">P193</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p204">P204</a></td>
</tr>
<tr>
<td><strong>LLM/Prompt-guided</strong></td>
<td style="text-align:center;">14</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p002">P002</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p013">P013</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p015">P015</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p023">P023</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p078">P078</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p081">P081</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p082">P082</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p090">P090</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p099">P099</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p101">P101</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p103">P103</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p104">P104</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p122">P122</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p127">P127</a></td>
</tr>
<tr>
<td><strong>Generation-based</strong></td>
<td style="text-align:center;">7</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p025">P025</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p028">P028</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p034">P034</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p036">P036</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p119">P119</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p143">P143</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p147">P147</a></td>
</tr>
<tr>
<td><strong>Metamorphic testing</strong></td>
<td style="text-align:center;">3</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p039">P039</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p041">P041</a>, <a href="{{ site.baseurl }}/results/primary-studies.html#p049">P049</a></td>
</tr>
<tr>
<td><strong>Debugging/Fault-localization</strong></td>
<td style="text-align:center;">1</td>
<td><a href="{{ site.baseurl }}/results/primary-studies.html#p050">P050</a></td>
</tr>

</tbody>
</table>

</div>

> **Note:** Technique-family labels are not mutually exclusive because some
> studies combine multiple central mechanisms. This table uses the normalized
> high-level labels used in RQ2. Original descriptive labels and normalization
> rationales are preserved in the annotated dataset available through the
> replication package.

## Interpretation

The mapping shows that mutation-based and coverage-guided techniques form the
largest and most widely combined families. Learning-based, constraint-guided,
search/heuristic-guided, differential, and LLM/prompt-guided mechanisms often
appear as complementary forms of generation, guidance, or failure detection.

The overlap across rows reflects the hybrid nature of AI-system fuzzing. A
single study may, for example, combine mutation with coverage feedback,
constraint-guided generation with differential testing, or LLM-based
generation with validation and comparison mechanisms.

The complete machine-readable annotations are available in the
[replication package on Zenodo](https://doi.org/10.5281/zenodo.21022814).
