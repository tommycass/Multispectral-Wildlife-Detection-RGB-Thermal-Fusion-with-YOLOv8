# Multispectral Wildlife Detection: RGB–Thermal Fusion with YOLOv8

**Authors:** Micol Michanie · Valentino Pettazi · Tomás Castro  
**Institution:** Universidad de San Andrés — AI Engineering (I308 Computer Vision)  
**Year:** 2025

---

## Overview

This project benchmarks multispectral object detection architectures for aerial wildlife monitoring, combining RGB and thermal drone imagery. We evaluate four fusion strategies on the **Aerial Wildlife Image Repository (AWIR)** dataset and achieve up to **mAP@50 = 0.987**.

---

## Architectures Evaluated

| Architecture | Strategy | Input |
|---|---|---|
| YOLOv8 RGB (baseline) | Unimodal | 3-ch RGB |
| YOLOv8 Thermal (baseline) | Unimodal | 3-ch (T,T,T) |
| YOLOv8 Early Fusion (HST/GST) | Early Fusion | Replace B channel with T |
| YOLOv8 Late Fusion (NMS) | Late Fusion | Dual stream + NMS |
| YOLOv8 RGB-T (n/s/m) | 4-channel | Modified stem Conv2d |
| YOLOv8 RGB-T + Adapter | Adapter | Conv2d→BN→SiLU projects 4→3 ch |

---

## Key Results (after re-labeling)

| Model | Precision | Recall | mAP@50 | mAP@50-95 |
|---|---|---|---|---|
| YOLOv8 RGB | 0.821 | 0.935 | 0.938 | 0.515 |
| YOLOv8 Thermal | 0.941 | 0.861 | 0.870 | 0.470 |
| Early Fusion | 0.932 | 0.919 | 0.981 | 0.554 |
| Late Fusion | 0.942 | 0.970 | 0.986 | 0.608 |
| YOLOv8-s RGB-T | 0.929 | 0.980 | 0.979 | 0.584 |
| **YOLOv8-n RGB-T + Adapter** | **0.932** | **0.985** | **0.987** | **0.559** |

---

## Dataset Re-labeling

A key contribution of this work is the identification and correction of systematic annotation gaps in the AWIR dataset. Using a fine-tuned **YOLOv11** model, we recovered **34 missing annotations** (32 cow, 1 deer, 1 horse) — instances that were penalizing correct detections as false positives.

---

## Dataset

**Aerial Wildlife Image Repository (AWIR)** — Mississippi State University  
3 species: cow, deer, horse | Aligned RGB–Thermal stereo pairs  
Split: 80% train / 10% val / 10% test → 123 / 16 / 17 pairs

Generalization validated on **SMOD** (SJTU Multispectral Object Detection) — 8,676 RGB-T pairs, urban scenarios, day/night.

---

## Stack

`Python` · `PyTorch` · `Ultralytics YOLOv8/v11` · `OpenCV` · `NumPy`

---

## Paper

Full paper available in this repository: [`Informe_TP_Final_Vision_Artificial.pdf`](./Informe_TP_Final_Vision_Artificial.pdf)

---

---

# Detección Multiespectral de Fauna con Fusión RGB-Térmica usando YOLOv8

**Autores:** Micol Michanie · Valentino Pettazi · Tomás Castro  
**Institución:** Universidad de San Andrés — Ingeniería en IA (I308 Visión Artificial)  
**Año:** 2025

---

## Descripción

Este proyecto evalúa arquitecturas de detección de objetos multiespectrales para monitoreo aéreo de fauna silvestre, combinando imágenes RGB y térmicas de drones. Se comparan cuatro estrategias de fusión sobre el dataset **AWIR (Aerial Wildlife Image Repository)**, alcanzando hasta **mAP@50 = 0.987**.

---

## Arquitecturas Evaluadas

| Arquitectura | Estrategia | Entrada |
|---|---|---|
| YOLOv8 RGB (baseline) | Unimodal | 3 canales RGB |
| YOLOv8 Térmico (baseline) | Unimodal | 3 canales (T,T,T) |
| YOLOv8 Early Fusion (HST/GST) | Fusión Temprana | Reemplaza canal B por T |
| YOLOv8 Late Fusion (NMS) | Fusión Tardía | Dual stream + NMS |
| YOLOv8 RGB-T (n/s/m) | 4 canales | Stem Conv2d modificado |
| YOLOv8 RGB-T + Adaptador | Adaptador | Conv2d→BN→SiLU proyecta 4→3 ch |

---

## Resultados Clave (tras re-etiquetado)

| Modelo | Precisión | Recall | mAP@50 | mAP@50-95 |
|---|---|---|---|---|
| YOLOv8 RGB | 0.821 | 0.935 | 0.938 | 0.515 |
| YOLOv8 Térmico | 0.941 | 0.861 | 0.870 | 0.470 |
| Early Fusion | 0.932 | 0.919 | 0.981 | 0.554 |
| Late Fusion | 0.942 | 0.970 | 0.986 | 0.608 |
| YOLOv8-s RGB-T | 0.929 | 0.980 | 0.979 | 0.584 |
| **YOLOv8-n RGB-T + Adaptador** | **0.932** | **0.985** | **0.987** | **0.559** |

---

## Re-etiquetado del Dataset

Una contribución clave de este trabajo es la identificación y corrección de inconsistencias sistemáticas en las anotaciones del dataset AWIR. Usando un modelo **YOLOv11** fine-tuneado, recuperamos **34 anotaciones faltantes** (32 cow, 1 deer, 1 horse) que penalizaban detecciones correctas como falsos positivos.

---

## Dataset

**Aerial Wildlife Image Repository (AWIR)** — Mississippi State University  
3 especies: vaca, ciervo, caballo | Pares estéreo RGB–Térmicos alineados  
Split: 80% entrenamiento / 10% validación / 10% test → 123 / 16 / 17 pares

Generalización validada en **SMOD** (SJTU Multispectral Object Detection) — 8.676 pares RGB-T, escenarios urbanos diurnos y nocturnos.

---

## Stack

`Python` · `PyTorch` · `Ultralytics YOLOv8/v11` · `OpenCV` · `NumPy`

---

## Paper

Paper completo disponible en este repositorio: [`Informe_TP_Final_Vision_Artificial.pdf`](./Informe_TP_Final_Vision_Artificial.pdf)
