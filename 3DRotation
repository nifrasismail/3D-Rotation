// Code By Nifras Ismail
#include <windows.h>
#include <gl/Gl.h>
#include <gl/glut.h>
#include <cmath> 

typedef struct{float x;float y;}Point2D;
typedef struct{float x;float y;float z;}Point3D;


Point3D A,B,C,D,E,F,G,H;	// Vertices of the cube

Point2D Projected_A,Projected_B,Projected_C,Projected_D,Projected_E,Projected_F,Projected_G,Projected_H;

GLfloat v_list[8][3];  /* Vertex list - will be filled in with X,Y,Z vertexes. */
GLint f_list[6][4];	/* Face list - for the 6 faces of a cube. */ 

void init(void)
{
	/* Setup the vertex-list and the face-list here*/
	v_list[0][0] = 100;
	v_list[0][1] = 100;
	v_list[0][2] = 100;

	v_list[1][0] = 300;
	v_list[1][1] = 100;
	v_list[1][2] = 100;

	v_list[2][0] = 300;
	v_list[2][1] = 300;
	v_list[2][2] = 100;

	v_list[3][0] = 100;
	v_list[3][1] = 300;
	v_list[3][2] = 100;

	v_list[4][0] = 100;
	v_list[4][1] = 100;
	v_list[4][2] = 300;

	v_list[5][0] = 300;
	v_list[5][1] = 100;
	v_list[5][2] = 300;

	v_list[6][0] = 300;
	v_list[6][1] = 300;
	v_list[6][2] = 300;

	v_list[7][0] = 100;
	v_list[7][1] = 300;
	v_list[7][2] = 300;


	
	

	

}

void rotatebox_x(float deg_x){		// rotate the cube about a line which is parallel to X axis 
	float ang = deg_x * 3.14159265359 / 180.0;		//angle in radians 
	
	for (int i = 0; i <= 7; i++) {		// do the necessary transformations for each of 8 vertices
		v_list[i][0] = v_list[i][0];
		v_list[i][1] = v_list[i][1]*cos(ang) - v_list[i][2]*sin(ang);
		v_list[i][2] = v_list[i][1]*sin(ang) + v_list[i][2]*cos(ang);
	}
	glutPostRedisplay();	//this will call the function "myDisplay()" again
}

void rotatebox_y(float deg_y){		// rotate the cube about a line which is parallel to Y axis 
	float ang = deg_y * 3.14159265359 / 180.0;
	
	for (int i = 0; i <= 7; i++) {		// do the necessary transformations for each of 8 vertices
		v_list[i][1] = v_list[i][1];
		v_list[i][0] = v_list[i][0]*cos(ang) - v_list[i][2]*sin(ang);
		v_list[i][2] = (-1)*v_list[i][0]*sin(ang) + v_list[i][2]*cos(ang);
	}
	glutPostRedisplay();	//this will call the function "myDisplay()" again
}

Point2D Project_ortho(float x, float y, float z){	//orthogonal projection
	Point2D p0;
	p0.x = x ;
	p0.y = y ;
	return p0;
}

void drawBox(Point2D A, Point2D B, Point2D C, Point2D D, Point2D E, Point2D F, Point2D G, Point2D H)
{
	// Just project the vertices and draw the box
	glPointSize(1.0);

	glBegin(GL_LINE_LOOP);	
	//DRAWING FRONT FACE
		glVertex2i(A.x, A.y); glVertex2i(B.x, B.y);	glVertex2i(C.x, C.y); glVertex2i(D.x, D.y);
	glEnd();

	glBegin(GL_LINE_LOOP);
	//DRAWING BACK FACE
		glVertex2i(E.x, E.y); glVertex2i(F.x, F.y);	glVertex2i(G.x, G.y); glVertex2i(H.x, H.y);
	glEnd();
	
	glBegin(GL_LINES);
	//DRAWING OTHER LINES
		glVertex2i(A.x, A.y); glVertex2i(E.x, E.y);

		glVertex2i(B.x, B.y); glVertex2i(F.x, F.y);

		glVertex2i(C.x, C.y); glVertex2i(G.x, G.y);

		glVertex2i(D.x, D.y); glVertex2i(H.x, H.y);
	glEnd();

	glFlush();
}

void draw_Cube(){
	Projected_A = Project_ortho(v_list[0][0],v_list[0][1],v_list[0][1]);
	Projected_B = Project_ortho(v_list[1][0],v_list[1][1],v_list[1][1]);
	Projected_C = Project_ortho(v_list[2][0],v_list[2][1],v_list[2][1]);
	Projected_D = Project_ortho(v_list[3][0],v_list[3][1],v_list[3][1]);
	Projected_E = Project_ortho(v_list[4][0],v_list[4][1],v_list[4][1]);
	Projected_F = Project_ortho(v_list[5][0],v_list[5][1],v_list[5][1]);
	Projected_G = Project_ortho(v_list[6][0],v_list[6][1],v_list[6][1]);
	Projected_H = Project_ortho(v_list[7][0],v_list[7][1],v_list[7][1]);

	drawBox(Projected_A,Projected_B,Projected_C,Projected_D,Projected_E,Projected_F,Projected_G,Projected_H);
	
}

void myDisplay()
{
	glClearColor(1.0f, 1.0f, 1.0f, 0.0f); 
	glClear(GL_COLOR_BUFFER_BIT);
	glColor3f(0.0f, 0.0f, 0.0f);
	draw_Cube();
}


void keyboard(unsigned char key, int x, int y)
{
	if (key == 'q' || key == 'Q')
		exit(EXIT_SUCCESS);
}

void special(int key, int, int) {
	switch (key) {
	case GLUT_KEY_LEFT: rotatebox_y(-1); break;	//	decreasing the angle by 1 degree
	case GLUT_KEY_RIGHT: rotatebox_y(1);break;	//	increasing the angle by 1 degree
	case GLUT_KEY_UP: rotatebox_x(-1);break;	//	decreasing the angle by 1 degree
	case GLUT_KEY_DOWN: rotatebox_x(1);break;	//	increasing the angle by 1 degree
	default: return;
	}
}

int main( int argc, char ** argv ) {
	glutInit( &argc, argv );
	glutInitWindowPosition( 0, 0 );
	glutInitWindowSize( 800, 600 );
	glutCreateWindow( "3D Transformations" );

	glMatrixMode( GL_PROJECTION ); 
	glLoadIdentity();
	gluOrtho2D( 0, 800, 0, 600 );
	glViewport(0, 0, 800, 600);

	init();

	glutKeyboardFunc(keyboard); 
	glutSpecialFunc(special);
	glutDisplayFunc( myDisplay );
	glutMainLoop();

	return( 0 );
}
