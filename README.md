# Snake Game AI with Reinforcement Learning

## 🐍 **Project Overview**

This project implements a Snake game controlled by an AI agent using reinforcement learning techniques. The agent is trained to play the game efficiently, maximizing its score by eating food while avoiding collisions with the walls and itself. The game environment is developed using **Pygame**, and the AI utilizes **Deep Q-Learning** for decision-making.

---

## 🧩 **Key Components**

### 1️⃣ **Game Environment**

The `SnakeGameAI` class defines the game logic and environment. Key features include:

- **Game Setup:**

  - The game is played on a grid with a customizable width and height.
  - The snake and food are represented as blocks on the grid.

- **Game Mechanics:**

  - The snake moves in one of four directions: `UP`, `DOWN`, `LEFT`, or `RIGHT`.
  - The game ends if the snake collides with the wall or itself.
  - The snake grows in size when it eats food, and the score increases accordingly.

- **Speed Adjustment:**
  - Players can dynamically adjust the game speed using the keyboard.

---

### 2️⃣ **AI Agent**

The `Agent` class implements the reinforcement learning logic for training the snake AI. Key responsibilities include:

- **State Representation:**

  - The game state is represented as a vector containing information about potential dangers, the snake's current direction, and the relative position of the food.

- **Action Selection:**

  - The agent selects actions based on an epsilon-greedy strategy to balance exploration and exploitation.

- **Memory Management:**

  - A replay memory is maintained to store experiences (`state`, `action`, `reward`, `next state`, `done`) for training.

- **Training:**
  - Short-term memory is used to train the model after each move.
  - Long-term memory is utilized to train the model using a batch of experiences.

---

### 3️⃣ **Neural Network**

The AI uses a feedforward neural network, implemented in the `LinearQnet` class, to predict the best action for a given state. The network is trained using the Q-learning algorithm, which updates the Q-values based on rewards received.

---

### 4️⃣ **Reward System**

The reward system encourages the AI to:

- Move closer to the food.
- Avoid collisions.
- Achieve higher scores by eating more food.

---

## ⚙️ **Implementation Details**

### **Game Logic**

- The game grid is divided into blocks of size `20x20` pixels.
- Food is randomly placed on the grid, ensuring it does not overlap with the snake.
- The game speed can be adjusted dynamically during gameplay by entering a new speed value.

---

### **AI Training Process**

1. **State Representation:**

   - The state vector includes:
     - Information about potential collisions in the current direction, and when turning left or right.
     - The snake's current direction.
     - The relative position of the food.

2. **Action Selection:**

   - Actions are encoded as one-hot vectors:
     - `[1, 0, 0]`: Continue straight.
     - `[0, 1, 0]`: Turn right.
     - `[0, 0, 1]`: Turn left.

3. **Training:**

   - A replay memory stores up to `100,000` experiences.
   - The agent is trained using mini-batches of experiences to minimize loss and improve decision-making.

4. **Reward Function:**
   - Rewards are assigned based on the following:
     - Positive reward for eating food.
     - Negative reward for collisions or failing to make progress.
     - Distance-based reward to encourage moving closer to the food.

---

### **Neural Network Architecture**

- **Input Layer:** 11 nodes (representing the state vector).
- **Hidden Layer:** 256 nodes.
- **Output Layer:** 3 nodes (representing possible actions).

---

## 🚀 **How to Run the Project**

1. **Create a virtual environment (Preferable):**

   ```bash
   virtualenv .env
   ```

2. **Activate the Virtual environment:**

   - **UNIX-based OS:**
     ```bash
     source ./.env/bin/activate
     ```
   - **Windows OS:**
     ```bash
     .\.env\Scripts\activate
     ```

3. **Install the dependencies:**

   ```bash
   pip install -r requirements.txt
   ```

4. **Run the game:**

   ```bash
   python agent.py
   ```

5. **Adjust the Speed as you like:**

   - Press `S` during gameplay to enter speed adjustment mode. Enter the desired speed and press `Enter`.
   - **Recommendation:** Keep the speed at its default value of `1000` for the first 100-150 tries, then slow it down to `20` to enjoy the view.

6. **Take a look at the chart of scores and the mean scores to see the progress:**
   - You can find the chart in the root directory of the project by the name of: `training_progress.png`.
   - **Note:** The image updates in real-time.

---

## 📈 **Visualization**

- A real-time chart tracks the agent's scores and average scores over time.
- **File:** `training_progress.png`

---

## 👨‍💻 **Author**

- **Name:** Fadi Bassam Alhabib
- **ID:** 202110663
- **Date:** 28, Dec, 2024
