# VetFlow — CLYVO VET

Sistema de gestão veterinária com um componente de Inteligência Artificial para cuidado contínuo do pet, desenvolvido como projeto da disciplina de Tecnologia em Desenvolvimento de Sistemas.
Solução desenvolvida para o **Challenge FIAP 2026** em parceria com a **CLYVO VET**.

## Integrantes do Grupo

| Nome | RM | Turma |
|------|----|-------|
| Andrei de Paiva Gibbini | 563061 | 2TDSPF |
| Pedro Sakai Silva Zambaca | 565956 | 2TDSPF |
| Pedro Santos Pequini | 561842 | 2TDSPF |
| Arthur Câmara | 562310 | 2TDSPG |
| Diogo Cunha | 563654 | 2TDSPF |

## Sobre o projeto

O VetFlow resolve o problema de tutores que só acionam a clínica veterinária de forma reativa (urgência, vacina vencida, sintoma agudo), o que gera baixa recorrência para a clínica, histórico clínico fragmentado e abandono de tratamentos. O sistema une cadastro, histórico e lembretes com um componente de IA que antecipa esse cuidado antes que vire urgência.

Documentação completa do componente de IA (problema, dados, estratégia de personalização e arquitetura): [`Documentacao_Tecnica.md`](./Documentacao_Tecnica.md).

---

## Módulos e Tecnologias

| Módulo | Tecnologia | Responsabilidade |
|---|---|---|
| App Mobile | React Native | Cadastro de pets, histórico, lembretes de vacinas/consultas |
| API Principal | Java · Spring Boot | Pets, tutores, consultas, vacinas, medicamentos, histórico clínico |
| API Complementar | .NET | Clínicas parceiras, agendamentos, notificações |
| Banco de Dados | Oracle | Modelagem relacional de todas as entidades |
| Componente de IA | Python · scikit-learn | Modelo preditivo de risco/priorização de cuidado |
| Infraestrutura | Docker + Azure (VM Linux) | Containerização e publicação da aplicação |
| Arquitetura Corporativa | TOGAF (Archi) | Camadas de visão, negócio, sistema e tecnologia |

---

## Estrutura do repositório

```
.
├── README.md
├── ai-prototipo/
│   ├── modelo_preditivo_prototipo.ipynb
│   └── exemplo_dados.csv
└── docs/
    ├── vetflow_pitch.pptx
    └── Documentacao_Tecnica.md

```

---

## Como rodar

### Pré-requisitos
- Java 17+ e Maven (API principal)
- .NET 8 SDK (API complementar)
- Node.js 18+ e npm/yarn (app mobile)
- Oracle Database (local ou instância na nuvem)
- Python 3.10+ (protótipo de IA)
- Docker (para subir os serviços containerizados)

### API principal (Java)
```bash
cd api-java
./mvnw spring-boot:run
```

### API complementar (.NET)
```bash
cd api-dotnet
dotnet run
```

### App mobile (React Native)
```bash
cd mobile
npm install
npm start
```

### Protótipo do componente de IA
Abra `ai-prototipo/modelo_preditivo_prototipo.ipynb` no [Google Colab](https://colab.research.google.com/) (Arquivo → Fazer upload de notebook) carregue o arquivo csv e execute todas as células — `numpy`, `pandas` e `scikit-learn` já vêm instalados no Colab por padrão. Também roda localmente em Jupyter:
```bash
pip install notebook scikit-learn pandas numpy --break-system-packages
jupyter notebook ai-prototype/predictive_model_prototype.ipynb
```

---

## Resultados parciais (Sprint 3)

- [x] Problema de negócio da IA definido e documentado (reatividade do tutor → baixa recorrência/LTV, histórico fragmentado, abandono de tratamentos).
- [x] Abordagem de IA escolhida e justificada tecnicamente: modelo preditivo.
- [x] Dados necessários identificados (origem, estrutura e uso) — ver `Documentacao_Tecnica.md`.
- [x] Estratégia de personalização documentada (score individual, priorização dinâmica, recomendação por contexto).
- [x] Diagrama arquitetural da integração IA ↔ app ↔ APIs ↔ banco.
- [x] Protótipo do modelo preditivo com dados sintéticos (`ai-prototipo/`).
- [ ] Integração do serviço de IA com as APIs Java/.NET em produção (próxima sprint).
- [ ] Treinamento do modelo com dados reais do Oracle (próxima sprint).
