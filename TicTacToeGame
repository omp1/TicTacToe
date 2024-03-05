package myfxdemo;

import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Cell;
import javafx.scene.control.Label;
import javafx.scene.layout.BorderPane;
import javafx.scene.layout.GridPane;
import javafx.scene.layout.Pane;
import javafx.scene.paint.Color;
import javafx.scene.shape.Ellipse;
import javafx.scene.shape.Line;
import javafx.stage.Stage;

public class TicTacToeGame extends Application {
	
	//static?
	private char currentLetter = 'O';
	private Cell[][] board = new Cell[3][3];
	private Label turn = new Label("O has to go");
	
	
	@Override
	public void start(Stage primaryStage) throws Exception{
		GridPane root = new GridPane();
		
		for (int i=0; i<3; i++) {
			for (int j=0; j<3; j++) {
				board[i][j] = new Cell();
				root.add(board[i][j], j, i);
			}
		}
		
//		Scene scene1 = new Scene(outer, 450, 300);
		
		BorderPane outer = new BorderPane();
	
		outer.setCenter(root);
		outer.setBottom(turn);
		
		Scene scene1 = new Scene(outer, 450, 450);
		primaryStage.setTitle("Tic-Tac-Toe");
		primaryStage.setScene(scene1);
		primaryStage.show();
		
		
	}
	
	public class Cell extends Pane {
		private char theLetter = ' ';
		
		public Cell() {
			setStyle("-fx-border-color : black");
			this.setPrefSize(300, 300);
			this.setOnMouseClicked(e -> handleClick());
			
		}
		
		private void handleClick() {
			// TODO Auto-generated method stub
			//adds letter to empty spot
			if (theLetter == ' ' && currentLetter != ' ') {
				setLetter(currentLetter);
				
				if (didWin(currentLetter)) {
					turn.setText(currentLetter + " won the game");
					currentLetter = ' ';
				}
				else if (fullBoard()) {
					turn.setText("Nobody won");
					currentLetter = ' ';
				}
				else {
					currentLetter = (currentLetter == 'O')?'X':'O';
					turn.setText(currentLetter + "'s turn");
				}
			}
			//return null;
		}

		public void setLetter(char x) {
			theLetter= x;
			
			if (theLetter == 'X') {
				Line line1 = new Line(10, 10, this.getWidth()-10, this.getHeight()-10);
				line1.endXProperty().bind(this.widthProperty().subtract(10));
				line1.endYProperty().bind(this.heightProperty().subtract(10));
				
				Line line2 = new Line(10, this.getHeight()-10, this.getWidth()-10, 10);
				line2.endXProperty().bind(this.widthProperty().subtract(10));
				line2.startYProperty().bind(this.heightProperty().subtract(10));
				
				
				getChildren().addAll(line1,line2);
			}
			else if(theLetter == 'O'){
				Ellipse ellipse = new Ellipse(this.getWidth()/2, this.getHeight()/2, this.getWidth()/2-10, this.getHeight()/2-10);
				ellipse.centerXProperty().bind(this.widthProperty().divide(2));
				ellipse.centerYProperty().bind(this.heightProperty().divide(2));
				ellipse.radiusXProperty().bind(this.widthProperty().divide(2).subtract(10));
				ellipse.radiusYProperty().bind(this.heightProperty().divide(2).subtract(10));
				ellipse.setStroke(Color.BLUE);
				ellipse.setFill(Color.RED);
				getChildren().add(ellipse);
			}
		}
		
		public char getTheLetter() {
			return theLetter;
		}
		
		
	}
	
	//theLetter is for the player
	public boolean didWin(char theLetter) {
		
		for (int i=0; i<3; i++) {
			//checks for 3 in a row
			if ((board[0][i].getTheLetter() == theLetter) &&(board[1][i].getTheLetter()==theLetter)&&(board[2][i].getTheLetter()==theLetter)) {
				return true;
			}
			
		}
		
		//diagonal check
		if ((board[0][0].getTheLetter() == theLetter) &&(board[1][1].getTheLetter()==theLetter)&&(board[2][2].getTheLetter()==theLetter)) {
			return true;
		}
		
		if ((board[0][2].getTheLetter() == theLetter) &&(board[1][1].getTheLetter()==theLetter)&&(board[2][0].getTheLetter()==theLetter)) {
			return true;
		}
		
		for (int i=0; i<3; i++) {
			
			if ((board[i][0].getTheLetter() == theLetter) &&(board[i][1].getTheLetter()==theLetter)&&(board[i][2].getTheLetter()==theLetter)) {
				return true;
			}
		}
		
		return false;
	}
	
	//checks board if there are empty spaces or not and returns value
	public boolean fullBoard() {
		for (int i=0; i<3; i++) {
			for (int j=0; j<3; j++) {
				if (board[i][j].getTheLetter() == ' ') {
					return false;
				}
			}
		}
		return true;
	}
	
	
	
	public static void main(String[] args) {
		launch(args);
	}
}

