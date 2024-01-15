# DATABASE:
## quiz table:

id: int
question: string
round: string
answers: string[]
correct_answer: string
image url: string | null

CREATE TABLE quiz (
    id INT GENERATED ALWAYS AS IDENTITY,
    question VARCHAR(100),
    round VARCHAR(100),
    answers VARCHAR(500),
    correct_answer VARCHAR(100),
    image_url VARCHAR(500),
    PRIMARY KEY (id)
);

INSERT INTO quiz (question, round, answers, correct_answer, image_url)
VALUES ('what is bail?', 'generalknowledge', '{"beef","autistic","green"}','autistic', 'none');


## player table:

id: int
name: string
global_score: int
host: bool

CREATE TABLE player (
    id INT GENERATED ALWAYS AS IDENTITY,
    name VARCHAR(100) UNIQUE NOT NULL,
    global_score INT NOT NULL,
    host BOOLEAN,
    PRIMARY KEY (id)
);

INSERT INTO player (name, global_score, host)
VALUES 
    ('boneur', 100, TRUE),
    ('reginald', 0,FALSE);


## quiz player table:

id: int
quiz_id: int foreign key
player_id: int foreign key
local_score: int

CREATE TABLE quizplayer (
    id INT GENERATED ALWAYS AS IDENTITY,
    quiz_id INT NOT NULL,
    player_id INT NOT NULL,
    local_score INT NOT NULL,
    PRIMARY KEY (id),
    FOREIGN KEY (quiz_id) REFERENCES quiz(id),
    FOREIGN KEY (player_id) REFERENCES player(id)
);

INSERT INTO quizplayer (quiz_id, player_id, local_score)
VALUES 
    (1,1,100),
    (1,2,0);