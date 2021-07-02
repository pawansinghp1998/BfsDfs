Q.1.(419).Given an m x n matrix board where each cell is a battleship 'X' or empty '.', return the number of the battleships on board.
Battleships can only be placed horizontally or vertically on board. In other words, they can only be made of the shape 1 x k (1 row, k columns) or k x 1 (k rows, 1 column), where k can be of any size. At least one horizontal or vertical cell separates between two battleships (i.e., there are no adjacent battleships).

Input: board = [["X",".",".","X"],[".",".",".","X"],[".",".",".","X"]]
Output: 2

Input: board = [["."]]
Output: 0

class Solution {
    public int countBattleships(char[][] board) {
        if(board==null || board.length==0) return 0;
         int ans=0;
        
        for(int i=0;i<board.length;i++){
            for(int j=0;j<board[0].length;j++){
                if(board[i][j]=='X'){
                    ans++;
                    dfs(board,i,j);
                }
            }
        }
        return ans;
    }
    
    public void dfs(char board[][],int i,int j){
        if(i>=board.length || j>=board[0].length || i<0 || j<0 || board[i][j]=='.') return;
        else{
            board[i][j]='.';
            
            dfs(board,i+1,j);
            dfs(board,i-1,j);
            dfs(board,i,j+1);
            dfs(board,i,j-1);
        }
    }
}
