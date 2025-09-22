# System Designing

System design is the process of designing the elements of a system such as the **architecture**, **modules and components**, the **interfaces** of those components, and the **data** that flows through the system.  

---

## High-Level Design (HLD)
High-Level Design provides an overview of the system architecture and the main components that would be developed for the resulting product.

- System architecture details  
- Database design  
- Services and processes  
- Relationships between various modules  

---

## Low-Level Design (LLD)
Low-Level Design describes the detailed design of each element mentioned in the High-Level Design.

- Classes  
- Interfaces  
- Relationships between different classes  
- Actual logic of various components  
# Monolithic Architecture

## What is Architecture?
**Architecture** refers to the internal design details used for building applications.

---

## What is Monolithic Architecture?
If all the components and functionalities of a project are **entangled and combined in a single codebase**, then that is a **Monolithic Application**.  

Monolithic Architecture is also known as a **Centralised System**.

---

## Key Characteristics
- All modules are combined into a single codebase  
- Deployed as **one unit**  
- Less complex to start with  
- Easier to understand → Higher productivity  

---

## When is Monolithic Architecture Good?
- When we are just **starting a project**  
- All modules are in a single system, so fewer **network calls** are needed compared to other architectures  
- Comparatively **easier to secure**  
- **Integration testing** is simpler  
- Less confusion for developers  

---

## Advantages
- Simpler to develop and deploy (especially for small projects)  
- Higher developer productivity in the early stages  
- Easier to test and secure  
- Reduced network overhead since everything is in one system  

---

## Disadvantages
- **Single point of failure**: if one module has a bug, the entire system can break  
- **Tightly coupled**: updating one module requires redeploying the entire system  
- **Technology lock-in**: changing the programming language or framework for one module affects the whole system  
- Harder to scale → you must scale the entire application, not just the part that needs more resources  

---
