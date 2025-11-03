# 1. Problem 1

In this part, we’re learning how to transpose matrices — basically flipping rows into columns, and columns into rows.

Define matrix X (just regular numbers)

	X = [2 0 1 8 0 -2; 3 4 7 3 7 6; -6 4 -1 2 5 9];
	
Different ways to transpose X

	transpose(X)   % Does the same thing as X.'
	
	X'             % Transpose + take the complex conjugate (used for complex numbers)
	
	X.'            % Regular transpose (doesn't take conjugates)


Define matrix Y (this time using complex numbers)

	Y = [(3+j.*2) (-6-j.*7) (1-j); (-5+j.*2) (3+j) (1+j.*7); (4-j.*3) (7+j.*8) (j.*3)];


	transpose(Y)   % Just flips rows and columns
	
	Y'             % Flips and also takes the complex conjugate
	
	Y.';           % Flips but doesn't take conjugates
	
# 2. Problem 2

In this part, we’ll solve a system of linear equations using the inverse matrix method and Cramer’s Rule.

Matrix A holds the coefficients of the equations

	A = [3 4 -3 pi 1 ; 1 -1 5 -4 6 ; 3 -5^(1/2) -1 7 -9; 7 4 -7 8 2; 9 csc(3) -11 (-6/5) 2];

b is the constants column on the right side of the equations

	b = [1; 12; -7; 2; 0];

Display a label for the Inverse Method solution

	disp('Solution using Inverse Method:')

Solve for x using the inverse of A (formula: x = inv(A)*b)

	x_inverse = inv(A)*b; % x = A⁻¹b
	
	disp(x_inverse)

Calculate the determinant of A

	detA = det(A);

Displays the determinant with 6 decimal places
	
	fprintf('\nDeterminant of A = %.6f\n', detA);

Check if determinant is zero (no unique solution if det(A) = 0)
	
	if det(A) == 0
     disp("No solution")
		
	else 
  	 n = length(b);  % Number of unknowns
  	 x = zeros(n,1); % Create space for answers

Loop through each variable (x1 to x5)

	for i = 1:n
        Ai = A;              % Copy A
        Ai(:,i) = b;         % Replace i-th column with b
        x(i) = det(Ai)/detA; % Formula for Cramer's Rule
    end

    disp('Solution using Cramer''s Rule:')
    disp(x)
	end
