# GAME-DEVELOPMENT-SNAKE-GAME

COMPANY: CODTECH IT SOLUTION

NAME: SAURABH KUMAR

INTERN ID: CT04DF95

DOMAIN: C++

DURATION: 4 WEEKS

MENTOR: NEELA SANTOSH

Snake Game Using SFML in C++ — Description
This C++ program is a classic implementation of the Snake game using the SFML (Simple and Fast Multimedia Library) framework. It demonstrates the principles of game development, including rendering, input handling, collision detection, audio management, and state resetting. The game is visually and interactively engaging, featuring smooth movement, growing mechanics, sound effects, and real-time scoring.

Core Concepts and Features
1. Game Window and Setup
The game window is created with a fixed resolution of 800x600 pixels, and the game grid uses cells of 20x20 pixels. This forms the playfield for the snake. The sf::RenderWindow object serves as the main rendering target. The frame rate is capped at 60 frames per second to ensure consistent performance.

cpp
Copy
Edit
sf::RenderWindow window(sf::VideoMode(WINDOW_WIDTH, WINDOW_HEIGHT), "Snake Game");
2. Snake Representation
The snake is represented as a list (std::vector) of sf::Vector2f objects, where each vector holds the position of a snake segment. The head of the snake moves in the current direction while the rest of the segments follow. The movement is grid-based to match the discrete nature of the game.

cpp
Copy
Edit
std::vector<sf::Vector2f> snake;
sf::RectangleShape snakeSegment;
3. Input and Direction Handling
The game listens for keyboard events to update the snake's direction. To avoid the snake from reversing into itself, it restricts changing to the opposite direction directly (e.g., from left to right immediately). The R key is used to reset the game after a game over.

4. Game Loop
The main game loop follows the classic structure:

Process Events: Checks for window close events and keyboard inputs.

Update: Moves the snake, checks for collisions, updates score and speed.

Render: Clears the screen, draws the snake, food, and score, then displays everything.

Game timing is controlled using an sf::Clock and elapsed time to regulate the snake’s movement independently of the frame rate.

Gameplay Logic
Snake Movement
The snake moves one cell per update tick. Each segment takes the position of the one before it, creating the slithering motion. The head moves in the current direction.

Food Collision and Growth
When the snake's head reaches the food's position, it plays a sound effect, increases the score, and grows by adding a new segment. The food is then respawned at a random position aligned to the grid.

cpp
Copy
Edit
snake.push_back(snake.back()); // Grow the snake
Wall and Self Collision
Wall Collision: If the snake's head moves outside the window bounds, the game ends.

Self Collision: If the head intersects any of the body segments, the game ends.

In both cases, a game over sound is played and a message is displayed with the option to restart.

Graphics and Audio
Snake Segments: Drawn as green rectangles using sf::RectangleShape.

Food: Represented as a red circle using sf::CircleShape.

Score Display: Uses an SFML font to render the score in the top-left corner.

Game Over Text: Rendered in red at the center when the player loses.

All assets (fonts and sounds) are loaded from the assets/ directory:

Font: arial.ttf

Sound effects: eat.wav, gameover.wav

Background music: background.ogg

Sound and Music Integration
The game includes rich audio feedback:

A background music loop provides atmosphere.

A "chomp" sound plays when the snake eats food.

A "game over" sound signals the end of the game.

These sounds enhance the player experience and provide real-time audio cues.

Difficulty and Speed Scaling
To make the game more engaging, the snake’s speed increases as the score rises:

cpp
Copy
Edit
speed = std::max(0.05f, 0.1f - score * 0.005f);
This introduces a natural difficulty curve as the player survives longer.

Conclusion
This SFML-based Snake Game in C++ is a polished, feature-rich implementation that captures the essence of the classic game while demonstrating modern programming concepts. It combines real-time graphics, user input, sound effects, and structured game logic into an enjoyable and extensible game framework. It serves both as a complete playable game and a solid foundation for learning or expanding into more advanced 2D game development.
