import turtle
Global_paddle_speed = 30

def move_up_paddle_right():
    y = pad_right.ycor()
    y +=Global_paddle_speed
    pad_right.sety(y)
    
def move_down_paddle_right():
    y = pad_right.ycor()
    y +=-Global_paddle_speed
    pad_right.sety(y)


def move_up_paddle_left():
    y = pad_left.ycor()
    y +=Global_paddle_speed
    pad_left.sety(y)

def move_down_paddle_left():
    y = pad_left.ycor()
    y +=-Global_paddle_speed
    pad_left.sety(y)

def set_object(obj, init_x_pos, is_ball):
    obj.speed(0)
    obj.shape("square")
    obj.color("white")
    if not is_ball:
        obj.shapesize(stretch_wid=5, stretch_len=1)
    else:
        obj.dx = 0.30
        obj.dy = -0.30
    obj.penup()
    obj.setpos(init_x_pos, 0)


def check_boundaries(obj,upper,lower,ext_right,ext_left,board):
    
    if obj.ycor() > upper or obj.ycor() < lower or obj.xcor() > ext_right or obj.xcor() < ext_left:

        if obj.ycor() > upper:
            obj.sety(upper)
            obj.dy *= -1   
        elif obj.ycor() < lower:
            obj.sety(lower)
            obj.dy *= -1
        elif obj.xcor() > ext_right:
            obj.goto(0,0)
            obj.dx *= -1
            score[0] +=1
            score_update(board,score)
            
        elif obj.xcor() < ext_left:
            obj.goto(0,0)
            obj.dx *= -1
            score[1] +=1
            score_update(board,score)
            

def check_collision(ball, pad_right, pad_left, window_width,):
    if ball.xcor() > (window_width//2 -60) and ball.xcor() < (window_width//2 -50) and ball.ycor() < (pad_right.ycor() + 50) and ball.ycor() > (pad_right.ycor() -50):
        ball.dx *= -1
    
    if ball.xcor() < (-window_width//2 +60) and ball.xcor() > (-window_width//2 +50) and ball.ycor() < (pad_left.ycor() + 50) and ball.ycor() > (pad_left.ycor() -50):
        ball.dx *= -1 

def score_update(board,score):
    board.clear()
    board.write("Player A:{}  Player B:{}".format(score[0],score[1]), align="center",font=("courier", 22,"normal")) 

#Instantiating my objects
pad_right = turtle.Turtle()
pad_left = turtle.Turtle()
ball = turtle.Turtle()

#Placing my objects in their initial positions
set_object(obj=pad_left, init_x_pos=-350, is_ball=False)
set_object(obj=pad_right, init_x_pos=350, is_ball=False)
set_object(obj=ball, init_x_pos=0, is_ball=True)

#Setting the window
my_width = 800
my_height = 600
ball_offset = 10
windows = turtle.Screen()
windows.title("My First Python Game")
windows.setup(width=my_width, height=my_height)
windows.bgcolor("black")
windows.tracer(0)

#Defining the boudaries
upper_bound =  my_height//2 - ball_offset
lower_bound = -my_height//2 + ball_offset
extreme_right = my_width//2 - ball_offset
extreme_left = -my_width//2 + ball_offset

#creating scores variables
score = [0,0]

#Moves For both paddles
windows.listen()
windows.onkeypress(move_up_paddle_right, "Up")
windows.onkeypress(move_down_paddle_right, "Down")
windows.onkeypress(move_up_paddle_left, "w")
windows.onkeypress(move_down_paddle_left, "s")

#Score Board
board = turtle.Turtle()
board.speed(0)
board.color("white")
board.penup()
board.setpos(0,250)
board.hideturtle()
score_update(board,score)

#Main loop
while(True):
    windows.update()

    #We move the ball
    ball.setx(ball.xcor() + ball.dx)
    ball.sety(ball.ycor() + ball.dy)

    check_boundaries(ball, upper_bound, lower_bound,extreme_right,extreme_left,board)
    check_collision(ball, pad_right, pad_left, my_width)
    
