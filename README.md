# part


    private int currentQuestion;
    private String [] questions;
    private String [] answers;
    private Button answerButton;
    private Button questionButton;
    private TextView questionView;
    private TextView answerView;
    private EditText answerText;


    public void init() {
        questions = new String[]{"In which city was the Titanic built?",
                "Which country sent its navy around the world to fight the Japanese in 1904?","1"};
        answers = new String[]{"Belfast","Russia","1"};
        currentQuestion = -1;
        answerButton = (Button)findViewById(R.id.AnswerButton);
        questionButton = (Button)findViewById(R.id.QuestionButton);
        questionView = (TextView) findViewById(R.id.QuestionTextView);
        answerView = (TextView) findViewById(R.id.AnswerTextView);
        answerText = (EditText) findViewById(R.id.AnswerText);
        answerButton.setOnClickListener(new OnClickListener(){
            @Override
            public void onClick(View v) {
                checkAnswer();
            }});
        questionButton.setOnClickListener(new OnClickListener(){
            @Override
            public void onClick(View v) {
                showQuestion();
            }});
    }


    public void showQuestion()
    {
        currentQuestion++;
        if(currentQuestion == questions.length)
            currentQuestion =0;
        questionView.setText(questions[currentQuestion]);
        answerView.setText("");
        answerText.setText("");
    }

    public boolean isCorrect(String answer)
    {
        return (answer.equalsIgnoreCase(answers[currentQuestion]));
    }

    public void checkAnswer()
    {
        String answer = answerText.getText().toString();
        if(isCorrect(answer))
            answerView.setText("You're right!");
        else
            answerView.setText("Sorry, the correct answer is "+answers[currentQuestion]);
    }





}



