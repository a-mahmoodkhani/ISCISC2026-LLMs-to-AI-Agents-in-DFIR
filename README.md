# From Large Language Models to AI Agents in Digital Forensics

Workshop materials presented at the **23rd International ISC Conference on Information Security and Cryptology (ISCISC 2026)**, **Amirkabir University of Technology**, Tehran, Iran.

**Presented by:** Amirmohammad Mahmoodkhani

This workshop examines how large language models and tool-using agents fit into digital forensic investigations. It traces the development of AI in the field, explains the architectures behind agentic workflows, and examines their practical use through a Windows forensic case study.

The practical study uses **one Windows E01 evidence image**, **26 investigative questions**, and **two configurations**: LLM-assisted AIFT and Autopsy extended with our custom **AI Investigator** plug-in.

[Materials](#materials) · [Workshop outline](#workshop-outline) · [Case study](#case-study) · [Autopsy plug-in](#ai-investigator-for-autopsy)

## Materials

| File | Description |
| --- | --- |
| [`slides/iscisc2026-workshop-slides.pdf`](slides/iscisc2026-workshop-slides.pdf) | Workshop slide deck covering all five parts of the presentation. |
| [`reports/aift-analysis-report.html`](reports/aift-analysis-report.html) | HTML forensic analysis report generated during the AIFT case study. |
| [`evaluation/aift-qwen3-8b-evaluation.pdf`](evaluation/aift-qwen3-8b-evaluation.pdf) | Question-by-question analysis of AIFT's responses to the 26 investigative questions using Qwen3-8B. |
| [`evaluation/autopsy-qwen3-14b-evaluation.pdf`](evaluation/autopsy-qwen3-14b-evaluation.pdf) | Question-by-question analysis of the agentic Autopsy configuration's responses to the same 26 questions using Qwen3-14B. |
| [`plugins/autopsy/ai-investigator.nbm`](plugins/autopsy/ai-investigator.nbm) | Compiled AI Investigator plug-in for Autopsy, developed for the workshop's agentic workflow. |

Start with the slides for the conceptual background, then read the two evaluation reports together to compare responses to the same questions. The AIFT HTML report provides the accompanying generated case analysis; download it and open it in a web browser.

## Workshop outline

### 1. Digital forensics and its challenges

An introduction to digital forensics, its purpose, and the stages of a digital investigation. A worked scenario connects those stages to practical investigative tasks and introduces the challenges that motivate the use of AI.

### 2. Large language models and agentics AI in digital forensics

A historical and architectural perspective on AI in forensic work: expert systems, machine learning, deep learning, large language models, and agentics AI.

Examples illustrate how language-model assistance extends into tool use and coordinated investigative actions. This part covers **tool-use patterns**, **ReAct**, and **planning**, followed by approaches to connecting agents to forensic tools through APIs and the **Model Context Protocol (MCP)**. These integration mechanisms provide access to tools; the surrounding control logic determines how an agent uses them.

### 3. The forensic tooling landscape

A survey of commercial and open-source forensic tools, including Belkasoft, Magnet Forensics, Autopsy, and AIFT. The discussion considers how language models and agentic capabilities are integrated into forensic workflows and compares the approaches presented.

### 4. Practical investigation and comparative evaluation

A worked case connects manual forensic examination with LLM-assisted and agentic analysis. Both configurations receive the same investigative questions, and their responses are compared with reference answers established from the manual investigation.

### 5. Conclusions and limitations

A discussion of the capabilities and limitations of the two evaluated configurations, with attention to the role of analyst verification and the limits of conclusions drawn from this case study.

## Case study

### Study design

We manually examined a Windows forensic disk image in E01 format using Autopsy, then prepared 26 investigative questions and recorded reference answers from the findings. Both evaluated configurations were asked the same questions.

Autopsy served two roles: the platform for the manual reference investigation and, with the custom plug-in, the platform for the agentic evaluation.

### Evaluated configurations

| Configuration | Workflow used in the workshop | Language model |
| --- | --- | --- |
| AIFT | LLM-assisted forensic analysis and question answering | Qwen3-8B |
| Autopsy + AI Investigator | Agentic investigation through our custom Autopsy plug-in | Qwen3-14B |

AIFT and Autopsy were selected because both are open-source forensic tools. Together, the selected configurations allowed the workshop to examine LLM-assisted analysis and an agentic extension to an established forensic platform.

The workflow labels describe the configurations evaluated in this workshop. Tool capabilities may vary across versions and deployments.

### Evaluation procedure

1. Examine the evidence manually and establish the reference findings.
2. Prepare the investigative questions and record their reference answers.
3. Submit the question set to each configuration and retain its responses.
4. Analyze the responses against the reference answers and compare the two configurations.
5. Document the question-level analysis in the two evaluation reports.

### Interpreting the comparison

This is a **case study of two system configurations**. Several factors constrain the conclusions that can be drawn:

- **Model size differs.** AIFT used an 8-billion-parameter model; the Autopsy configuration used a 14-billion-parameter model. Differences in their responses cannot be attributed to agentic architecture alone.
- **The forensic workflows also differ.** Each response reflects the complete configuration, including the model, the forensic processing workflow, and the information made available to it.
- **Coverage is case-specific.** One Windows image and 26 questions provide a basis for examining these runs. Broader claims require additional cases, question sets, and controlled experiments.
- **The reference analysis has its own scope.** Reference answers depend on the coverage and accuracy of the manual forensic examination.

Any investigative conclusion drawn from generated output should be checked against the underlying evidence.

### Reproducibility

Reproducing the runs requires the original evidence image and the corresponding software versions, plug-in build, model builds and quantization, prompts, inference settings, and environment configuration. These details matter when comparing a new run with the workshop results.

The materials listed above provide the presentation, reports, and compiled plug-in used to document and share the workshop study.

## AI Investigator for Autopsy

**AI Investigator** is the custom Autopsy plug-in developed for this workshop. It provided the agentic integration used with Qwen3-14B in the practical evaluation.

The plug-in is distributed as a compiled **NetBeans Module**:

[`plugins/autopsy/ai-investigator.nbm`](plugins/autopsy/ai-investigator.nbm)

### Standard NBM installation

1. Download `ai-investigator.nbm`.
2. In Autopsy, open **Tools → Plugins**.
3. Select **Downloaded → Add Plugins** and choose the NBM file.
4. Follow the installation prompts and restart Autopsy if requested.

These steps follow Autopsy's [NBM installation procedure](https://www.sleuthkit.org/autopsy/docs/user-docs/4.22.0/module_install_page.html). Autopsy compatibility, dependencies, and language-model configuration depend on the plug-in build; the steps above cover module installation.

## Related projects and references

- [ISCISC 2026](https://iscisc2026.aut.ac.ir/) — conference website.
- [Autopsy](https://github.com/sleuthkit/autopsy) — forensic platform used for the manual investigation and the custom agentic configuration.
- [AIFT](https://github.com/FlipForensics/AIFT) — forensic tool used for the LLM-assisted configuration.
- [Qwen3](https://qwenlm.github.io/blog/qwen3/) — model family used in both evaluated configurations.
- [ReAct: Synergizing Reasoning and Acting in Language Models](https://react-lm.github.io/) — research on interleaving reasoning and actions in language-model systems.
- [Model Context Protocol](https://modelcontextprotocol.io/docs/getting-started/intro) — protocol for connecting AI applications to external tools and data sources.

## License and attribution

The original workshop materials and the AI Investigator plug-in may be used, copied, and redistributed, provided that you credit the presenter(s) named above and cite this repository as the source. This attribution must be retained in redistributed copies.

When using the evaluation in research or teaching, please also cite the relevant workshop report.

Third-party tools, models, libraries, and other materials remain subject to their respective licenses.
