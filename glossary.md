---
title: Glossary - LLM Confidence
nav_order: 2
---

# Glossary

---

## Accuracy {#accuracy}
How close an answer is to the truth.

---

## Ambiguity {#ambiguity}
When language can be understood in more than one way.

---

## Approximation {#approximation}
A simplification in a model that introduces error.

---

## Uncertainty Band {#uncertainty-band}
<div id="band"></div>
<div id="band-uncertainty-band"></div>
A shaded area around a curve showing uncertainty in estimates.

---

## Bootstrap {#bootstrap}
A resampling technique used to measure uncertainty by running the model many times on slightly different samples of the same data.

---

## Calibration {#calibration}
How well predicted probabilities match observed outcomes.  
Clinical models target calibration; LLMs are often uncalibrated.

---

## Chain-of-Thought (CoT) {#chain-of-thought}
<div id="cot"></div>
A prompting strategy that asks the model to show step-by-step reasoning.  
Improves transparency but not necessarily accuracy; can create an illusion of expertise.

---

## Confidence Interval {#confidence-interval}
<div id="ci"></div>
<div id="ci-confidence-interval"></div>
A range of plausible values for a statistic (e.g., 0.28–0.44).  
Narrower intervals indicate higher precision.

---

## Consistency {#consistency}
Stability of answers across repeated prompts or small variations.  
Higher consistency suggests higher confidence.

---

## Consistency-Based Confidence {#consistency-based-confidence}
A measure of how stable the model’s answers are across repeated queries.  
High similarity across runs implies higher confidence.

---

## Correctness {#correctness}
Agreement between an answer and external truth or ground reality.

---

## Coverage {#coverage}
Whether training or reference data include the needed cases or facts.

---

## Cox Model {#cox}
A classical statistical model for risk over time used in survival analysis.

---

## Decision Path {#decision-path}
The internal route a model takes to reach a prediction.

---

## Hazard Ratio Decomposition {#decomposition-hazard-ratio}
<div id="hazard-ratio-decomposition"></div>
Breaking a risk estimate into feature-level contributions.

---

## Disclaimer {#disclaimer}
Text that qualifies an answer (e.g., uncertainty statements or warnings).

---

## Dissonance {#dissonance}
Mismatch between perceived confidence and actual accuracy.

---

## Distribution (Outcome) {#distribution}
<div id="outcome-distribution"></div>
How observed results are spread across possible values.

---

## Ensemble {#ensemble}
A set of multiple models queried for the same task.  
Agreement across models suggests higher confidence.

---

## Ensemble-Based Confidence {#ensemble-based-confidence}
Confidence inferred from agreement across different models.  
Agreement increases confidence; disagreement indicates uncertainty.

---

## Entropy {#entropy}
A measure of uncertainty in the model’s predictions.  
Low entropy: the model strongly prefers one token.  
High entropy: many tokens are similarly likely.

---

## Evaluation (Internal) {#evaluation-internal}
Developer-facing assessment of model performance, safety, and stability.

---

## Explanation {#explanation}
Text that clarifies how or why a result was produced.

---

## Explanation Quality {#explanation-quality}
A metric assessing clarity, usefulness, and correctness of an explanation.

---

## Failure Mode {#failure-mode}
A systematic way in which a model produces errors.

---

## Faithfulness {#faithfulness}
Staying true to the model’s internal reasoning or structure in an explanation.

---

## Feature {#feature}
An input variable used by a model to make predictions.

---

## Framing {#framing}
How information is presented to shape perception and trust.

---

## Hazard {#hazard}
Risk of an event occurring at a given time point (in survival analysis).

---

## Hazard Ratio {#hazard-ratio}
Relative risk comparing two groups; often reported with a confidence interval.

---

## Feature Importance {#feature-importance}
<div id="importance"></div>
Estimated contribution of a feature to a prediction.

---

## Conversational Interface {#interface-conversational}
<div id="interface"></div>
A chat-like system for interactive explanations and follow-up questions.

---

## LIME {#lime}
A method explaining predictions by fitting simple local surrogate models.

---

## Linguistic {#linguistic}
Related to language form and expression, not necessarily factual truth.

---

## Linguistic Authority {#linguistic-authority}
Persuasive force derived from confident language and presentation.

---

## LLM (Large Language Model) {#llm}
<div id="large-language-model"></div>
An AI system trained on huge amounts of text to generate language that sounds human (e.g., ChatGPT).  
It predicts what words are likely to come next based on patterns in language, not stored facts.

---

## LLM API {#llm-api}
An interface to interact programmatically with an LLM by sending parameters that control responses.  
Used to study and modify model behavior.

---

## Log-Likelihood {#log-likelihood}
The sum of all log probabilities across a sentence.  
Indicates how likely the full sequence is according to the model.

---

## Logprobs {#logprobs}
A numerical measure of how likely the model thinks a token is in context.  
Higher logprob implies a more confident choice.  
Expressed on a logarithmic scale.

---

## Max Tokens {#max-tokens}
The maximum length of the model’s response.  
Affects detail and risk of hallucination (long answers can drift).

---

## Measurement Error {#measurement-error}
Inaccuracy from instruments, data collection, or labeling.

---

## Meta-Model {#meta-model}
A model that evaluates or manages other models (e.g., judges answer correctness).

---

## Meta-Textual {#meta-textual}
About how something is said, not the underlying facts.

---

## Meta-Textual Confidence {#meta-textual-confidence}
Confidence conveyed by wording and tone rather than statistical measures.

---

## Narrative Summary {#narrative-summary}
A concise, human-readable explanation tailored to a professional audience.

---

## Outlier {#outlier}
An answer or data point that deviates markedly from the rest.

---

## Overreliance {#overreliance}
Trusting a system more than warranted, especially when it sounds confident but is wrong.

---

## Point Estimate {#point-estimate}
A single, precise prediction (e.g., 0.36).  
Does not express uncertainty.

---

## Predictive Distribution {#predictive-distribution}
A range of possible outcomes, each with its own probability.

---

## Predictive Model {#predictive-model}
A mathematical system that predicts a future event based on observed data.

---

## Reliability {#reliability}
Consistency and dependability of outputs over time and conditions.

---

## Robustness {#robustness}
Reliability of answers under re-prompting, perturbations, or model changes.

---

## Saliency Map {#saliency-map}
A visualization highlighting input regions most influential for a prediction.

---

## Standard Error (SE) {#standard-error}
<div id="se"></div>
Estimated variability of a statistic across repeated samples.

---

## Sequence {#sequence}
The full string of tokens in an answer.

---

## SHAP {#shap}
A method assigning credit to features for a prediction using game-theoretic values.

---

## Standard Deviation {#standard-deviation}
A measure of how much predictions vary.  
Higher values imply more uncertainty; lower values imply more consistency.

---

## Survival Curve {#survival-curve}
A graph of the probability of surviving beyond a given time, often with uncertainty bands.

---

## Survival Model {#survival-model}
A predictive model estimating the probability that something happens over time.

---

## Temperature {#temperature}
A parameter controlling how creative or predictable answers are.

---

## Token {#token}
The smallest unit of text used by the model (word, subword, or punctuation).

---

## Top-p (Nucleus Sampling) {#top-p}
<div id="nucleus-sampling"></div>
A randomness control limiting token choice to the most probable subset of tokens.

---

## Training Data {#training-data}
Text used to teach an LLM.

---

## Truth {#truth}
Conformity to facts about the world.

---

## Underreliance {#underreliance}
Distrusting correct answers due to cautious tone or low stated confidence.

---

## Variance {#variance}
How spread out results are around an average.

---

## Warnings {#warnings}
Explicit cautions about uncertainty, limitations, or risks.

---

## Weight {#weight}
A learned parameter controlling a feature’s influence.

---

## XAI (Explainable AI) {#xai}
Techniques that make models and their outputs interpretable.

