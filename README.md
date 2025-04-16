# 🧠 OptiLearn — AI-Based Subject Recommendation System with Burnout Prediction

OptiLearn is a full-stack AI-powered subject recommendation system that helps students plan their academic journey while minimizing the risk of burnout. It intelligently suggests personalized course schedules by combining burnout risk modeling, semantic outcome alignment, and multi-objective optimization.

## 🔧 Tech Stack

- **Frontend**: [SvelteKit](https://kit.svelte.dev/) — Lightweight, high-performance frontend framework  
- **Backend**: [FastAPI](https://fastapi.tiangolo.com/) — Python-based async API framework  
- **Database**: PostgreSQL — Structured storage for users, courses, and planning metadata  
- **Vector Search**: [Pinecone](https://www.pinecone.io/) — Real-time vector similarity search for course-outcome alignment  
- **Machine Learning**: [Scikit-learn](https://scikit-learn.org/) — Burnout prediction model using regression  
- **Optimization**: Genetic Algorithm (custom implementation) — To generate optimal course schedules  

## 🚀 Features

- 📚 **Course Recommendation**: Suggests optimal subjects based on interests, proficiency, and learning goals  
- 🔥 **Burnout Risk Prediction**: Uses a scikit-learn regression model based on workload, grades, and stress  
- 🧬 **Genetic Algorithm Optimization**: Finds optimal course combinations over 4 semesters  
- 🎯 **Semantic Outcome Alignment**: Uses sentence embeddings + Pinecone to match user goals with course outcomes  
- 🗃 **PostgreSQL Integration**: Stores user profiles, course metadata, and planning logic  

## 🧩 System Architecture

```plaintext
[SvelteKit Frontend]
        ↓
[FastAPI Backend] ←→ [Scikit-learn Model for Burnout]
        ↓
[PostgreSQL Database]
        ↓
[Pinecone Vector Search] ←→ [Course Embeddings + User Goal Embeddings]
```

## 📈 Utility Function

Each recommended course is scored using:

```
U = α · Interest + β · (1 − Burnout Score) + γ · Outcome Alignment Score
```

Where:
- Burnout Score is predicted using scikit-learn
- Outcome Alignment is computed via Pinecone vector similarity
- α, β, γ are tunable weights for multi-objective optimization

## 🛠️ Installation & Running Locally

1. Clone the repository
```bash
git clone https://github.com/your-username/optilearn.git
cd optilearn
```

2. Backend Setup (FastAPI + Python)
```bash
cd backend
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
uvicorn main:app --reload
```

3. Frontend Setup (SvelteKit)
```bash
cd frontend
npm install
npm run dev
```

4. Set up PostgreSQL and Pinecone
- Create a PostgreSQL database and update connection strings in .env
- Add your Pinecone API key and environment to backend .env

## 📊 Example Use Case

1. User provides learning goals (e.g., AI, Data Science), proficiency, and available study hours
2. System predicts burnout for each subject using workload and grade stress
3. Pinecone compares user goals with course outcomes via sentence embeddings
4. Genetic Algorithm selects optimal subjects across 4 semesters
5. Personalized schedule is returned with burnout-safe paths

## 📅 Future Enhancements

- Add real-time stress tracking (e.g., via wearable APIs)
- Use LangChain + GPT for conversational recommendations
- Feedback-based tuning of GA weights and burnout thresholds
- Admin dashboard to curate and manage course database

## 🙌 Acknowledgements

- Scikit-learn for ML modeling
- Pinecone for lightning-fast vector similarity search
- DEAP for genetic algorithm concepts
- Inspired by academic research on burnout and student stress modeling

## 📄 License

MIT License — feel free to use, modify, or contribute!