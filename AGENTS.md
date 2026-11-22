# Documentation writing guidelines

These instructions apply to documentation and technical articles in `content.en/` and `content.id/`, including Maya/rigging, Python, licensing, Hugo, and cloud architecture (AWS, serverless, infrastructure, and related topics).

## Audience and tone

- Write for a broad technical readership, not as a personal conversation with a single reader.
- Keep the tone natural, fluent, approachable, and professional. Impersonal does **not** mean stiff, legalistic, or excessively passive.
- Avoid second-person address in user-facing documentation: **you, your, yours** in English and **kamu, Anda, kalian**, or possessive **-mu** in Indonesian. Avoid conversational **kita** and **we** in procedural documentation unless a first-person narrative is explicitly requested.
- Prefer short active statements, clear subject-based descriptions, and concise imperative steps. Imperatives such as "Select the mesh and click Load Mesh" are natural and do not require a pronoun.
- Explain what a control, service, or operation does, when it matters, and what result to expect. Avoid filler, sales language, robotic transitions, and unnecessary repetition.
- Match technical depth to the article's audience. Maya tutorials assume rigging artists and technical artists know skinCluster, influences, vertices, weights, and other common Maya terms. Cloud architecture articles can assume familiarity with AWS, IAM, Lambda, API Gateway, DynamoDB, IaC, and related concepts when appropriate. Do not dilute technically accurate material into beginner-level prose.

## English

- Prefer reader-neutral phrasing. Example: "Download the package built for the required Maya version and operating system" instead of "Download the package for your Maya version".
- For architecture documentation, prefer "The Lambda function validates the webhook signature before writing to DynamoDB" over "Your Lambda should validate the webhook signature".
- Keep established technical terminology and exact UI/button labels. Use Australian/British spelling consistently where natural (for example, licence, centre, colour).

## Bahasa Indonesia

- Gunakan kalimat yang natural untuk khalayak umum, tanpa menyapa satu pembaca secara personal.
- Contoh: "Download ZIP yang sesuai dengan versi Maya, sistem operasi, dan arsitektur prosesor yang akan digunakan"; hindari "yang kamu gunakan".
- Gunakan kata kerja langsung untuk instruksi, misalnya "Pilih mesh, lalu klik Load Mesh". Kalimat tidak perlu dibuat pasif hanya untuk menghindari kata ganti orang.
- Istilah teknis yang lazim digunakan oleh praktisi (misalnya skinCluster, influence, vertex, skin weights, webhook, IAM, dan deployment) boleh tetap dalam bahasa Inggris. Hindari terjemahan harfiah yang membuat kalimat janggal.

## Accuracy and Hugo content

- Editorial changes must not silently change software behavior, licensing rules, workflow scope, warnings, default values, or examples.
- Preserve front matter (especially `translationKey`), Markdown structure, code blocks, Hugo shortcodes, image/GIF paths, and internal links unless a change is explicitly requested.
- Keep the English and Indonesian versions semantically aligned; natural localization matters more than word-for-word translation.
- Make factual claims about cloud services and evolving platform features only after checking reliable current documentation.

## Explicit wording exception

The following two lines in `content.en/documentation/ad-skin-tool-tutorial.md` were explicitly requested to remain in their original wording. Preserve them verbatim unless directly instructed otherwise, even though the first contains a second-person possessive:

> This guide walks through the controls in AD Skin Tool and explains how each one affects your Maya scene.

> 6. Read the status message after every operation. Detailed diagnostics are also printed in Maya's Script Editor.
