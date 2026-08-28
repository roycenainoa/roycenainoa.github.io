---
layout: project
type: project
image: img/gym-reporter.png
title: "Gym Equipment Issue Reporter"
date: 2026
published: true
labels:
  - Python
  - FastAPI
  - React
  - Docker
  - SQLite
summary: "A full-stack web app for reporting and tracking broken gym equipment — members submit tickets, facility managers triage and resolve them."
---

## About

The Gym Equipment Issue Reporter is a full-stack web application that lets gym members report broken or faulty equipment and lets facility managers track and resolve those reports. A member submits a ticket describing the issue; a manager sees the queue, updates its status, and closes it out. It was built for the DLMCSPSE01 portfolio.

## Stack and design

- **Frontend:** React + Tailwind CSS (Vite)
- **Backend:** Python + FastAPI, with an auto-generated OpenAPI / Swagger UI
- **Database:** SQLite via the SQLAlchemy ORM, seeded with realistic equipment and sample tickets on first start
- **Containerization:** Docker + docker-compose, deployed as a single service

## Learning outcome

Building this end to end reinforced how the pieces of a full-stack app fit together — designing a REST API, modeling the data, wiring a typed frontend to it, and packaging the whole thing in Docker so it runs the same anywhere.

[Live demo](https://gym-reporter-api.onrender.com) · [Source on GitHub](https://github.com/roycenainoa/gym-equipment-issue-reporter)
