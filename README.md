// Programas-metodos//
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

void caratula()
{
    printf("\tPrograma: Metodos abiertos\n\n\n");
    printf("\tObjetivo: Calcular las raices de una funcion por el metodo de la secante y newton\n\n\n");
    printf("\tEquipo 9\n\n\n");
    printf("\tIntegrantes:\n\n\n");
    printf("\tRivera Rodas Diego\n\tFajardo Herrera Victor Manuel\n\n");
    system("pause");
    system("cls");
}

int menu()
{
    int opcion;

    system("cls");
    printf("\t\t\tEscoge una funcion\n");

    printf("1°: x^2 * cos(x) - 2x\n");
    printf("2°: (6 - (2/x^2)) * ((exp(2+x) ) / 4) + 1\n");
    printf("3°: (x^3) - (3sin(x^2)) + 1\n");
    printf("4°: (x^3) + 6x^2 + 9.4x + 2.5\n");
    printf("5°: Salir\n");
    do
    {
        printf("Opcion: ");
        scanf("%d", &opcion);
    } while (opcion < 1 || opcion > 5);

    return opcion;
}

int menu2()
{
    int opcion;

    system("cls");
    
    printf("\t\t\tCon que metodo deseas calcular la raiz\n");

    printf("1°: Secante\n");
    printf("2°: Newton\n");
    do
    {
        printf("Opcion: ");
        scanf("%d", &opcion);
    } while (opcion < 1 || opcion > 2);
	system("cls");
    return opcion;
}

double f_sec_1(double x)
{
    return x * x * cos(x) - 2 * x;
}

double secante1(double x0, double x1, double tol, int max_iter)
{
    double x2, error, fx0, fx1;
    int iter = 0;

    printf("Iter\tX0\t\tX1\t\tf(x0)\t\tf(X1)\t\tx2\t\tf(X2)\t\tError\n");

    do
    {
        fx0 = f_sec_1(x0);
        fx1 = f_sec_1(x1);

        x2 = x1 - (fx1 * (x1 - x0)) / (fx1 - fx0);
        error = fabs((x2 - x1) / x2);

        printf("%d\t%.6lf\t%.6lf\t%.6lf\t%.6lf\t%.6lf\t%.6lf\t%.6lf\n", iter, x0, x1, fx0, fx1, x2, f_sec_1(x2), error);

        x0 = x1;
        x1 = x2;
        iter++;

        if (iter >= max_iter)
        {
            printf("\nSe alcanzo el numero maximo de iteraciones.\n");
            return x2;
        }
    } while (error > tol);

    return x2;
}

void p_secante_1()
{
    double x0, x1, tol, raiz;
    int max_iter, opcion;

    do
    {
        printf("Ingrese el valor inicial x0: ");
        scanf("%lf", &x0);

        printf("Ingrese el valor inicial x1: ");
        scanf("%lf", &x1);

        printf("Ingrese la tolerancia: ");
        scanf("%lf", &tol);

        printf("Ingrese el numero maximo de iteraciones: ");
        scanf("%d", &max_iter);

        raiz = secante1(x0, x1, tol, max_iter);

        printf("\nLa raiz aproximada es %.6lf\n", raiz);

        printf("\nDesea encontrar otra raiz? (1 para si, 0 para no): ");
        scanf("%d", &opcion);

    } while (opcion == 1);
}

double f_sec_2(double x)
{
    return (6 - (2 / (x * x))) * ((exp(2 + x)) / 4) + 1;
}

double secante2(double x0, double x1, double tol, int max_iter)
{
    double x2, error, fx0, fx1;
    int iter = 0;

    printf("Iter\tX0\t\tX1\t\tf(x0)\t\tf(X1)\t\tx2\t\tf(X2)\t\tError\n");

    do
    {
        fx0 = f_sec_2(x0);
        fx1 = f_sec_2(x1);

        x2 = x1 - (fx1 * (x1 - x0)) / (fx1 - fx0);
        error = fabs((x2 - x1) / x2);

        printf("%d\t%.6lf\t%.6lf\t%.6lf\t%.6lf\t%.6lf\t%.6lf\t%.6lf\n", iter, x0, x1, fx0, fx1, x2, f_sec_2(x2), error);

        x0 = x1;
        x1 = x2;
        iter++;

        if (iter >= max_iter)
        {
            printf("\nSe alcanzo el numero maximo de iteraciones.\n");
            return x2;
        }
    } while (error > tol);

    return x2;
}

void p_secante_2()
{
    double x0, x1, tol, raiz;
    int max_iter, opcion;

    do
    {
        printf("Ingrese el valor inicial x0: ");
        scanf("%lf", &x0);

        printf("Ingrese el valor inicial x1: ");
        scanf("%lf", &x1);

        printf("Ingrese la tolerancia: ");
        scanf("%lf", &tol);

        printf("Ingrese el numero maximo de iteraciones: ");
        scanf("%d", &max_iter);

        raiz = secante2(x0, x1, tol, max_iter);

        printf("\nLa raiz aproximada es %.6lf\n", raiz);

        printf("\n¿Desea encontrar otra raiz? (1 para si, 0 para no): ");
        scanf("%d", &opcion);

    } while (opcion == 1);
}

double f_sec_3(double x)
{
    return (x * x * x) - (3 * sin(x * x)) + 1;
}

double secante3(double x0, double x1, double tol, int max_iter)
{
    double x2, error, fx0, fx1;
    int iter = 0;

    printf("Iter\tX0\t\tX1\t\tf(x0)\t\tf(X1)\t\tx2\t\tf(X2)\t\tError\n");

    do
    {
        fx0 = f_sec_3(x0);
        fx1 = f_sec_3(x1);

        x2 = x1 - (fx1 * (x1 - x0)) / (fx1 - fx0);
        error = fabs((x2 - x1) / x2);

        printf("%d\t%.6lf\t%.6lf\t%.6lf\t%.6lf\t%.6lf\t%.6lf\t%.6lf\n", iter, x0, x1, fx0, fx1, x2, f_sec_3(x2), error);

        x0 = x1;
        x1 = x2;
        iter++;

        if (iter >= max_iter)
        {
            printf("\nSe alcanzo el numero maximo de iteraciones.\n");
            return x2;
        }
    } while (error > tol);

    return x2;
}

void p_secante_3()
{
    double x0, x1, tol, raiz;
    int max_iter, opcion;

    do
    {
        printf("Ingrese el valor inicial x0: ");
        scanf("%lf", &x0);

        printf("Ingrese el valor inicial x1: ");
        scanf("%lf", &x1);

        printf("Ingrese la tolerancia: ");
        scanf("%lf", &tol);

        printf("Ingrese el numero maximo de iteraciones: ");
        scanf("%d", &max_iter);

        raiz = secante3(x0, x1, tol, max_iter);

        printf("\nLa raiz aproximada es %.6lf\n", raiz);

        printf("\n¿Desea encontrar otra raiz? (1 para si, 0 para no): ");
        scanf("%d", &opcion);

    } while (opcion == 1);
}

double f_sec_4(double x)
{
    return (x * x * x) + (6 * (x * x)) + (9.4 * x) + 2.5;
}

double secante4(double x0, double x1, double tol, int max_iter)
{
    double x2, error, fx0, fx1;
    int iter = 0;

    printf("Iter\tX0\t\tX1\t\tf(x0)\t\tf(X1)\t\tx2\t\tf(X2)\t\tError\n");

    do
    {
        fx0 = f_sec_4(x0);
        fx1 = f_sec_4(x1);

        x2 = x1 - (fx1 * (x1 - x0)) / (fx1 - fx0);
        error = fabs((x2 - x1) / x2);

        printf("%d\t%.6lf\t%.6lf\t%.6lf\t%.6lf\t%.6lf\t%.6lf\t%.6lf\n", iter, x0, x1, fx0, fx1, x2, f_sec_4(x2), error);

        x0 = x1;
        x1 = x2;
        iter++;

        if (iter >= max_iter)
        {
            printf("\nSe alcanzo el numero maximo de iteraciones.\n");
            return x2;
        }
    } while (error > tol);

    return x2;
}

void p_secante_4()
{
    double x0, x1, tol, raiz;
    int max_iter, opcion;

    do
    {
        printf("Ingrese el valor inicial x0: ");
        scanf("%lf", &x0);

        printf("Ingrese el valor inicial x1: ");
        scanf("%lf", &x1);

        printf("Ingrese la tolerancia: ");
        scanf("%lf", &tol);

        printf("Ingrese el numero maximo de iteraciones: ");
        scanf("%d", &max_iter);

        raiz = secante4(x0, x1, tol, max_iter);

        printf("\nLa raiz aproximada es %.6lf\n", raiz);

        printf("\nDesea encontrar otra raiz? (1 para si, 0 para no): ");
        scanf("%d", &opcion);

    } while (opcion == 1);
}

double f_new_1(double x)
{
    return x * x * cos(x) - 2 * x;
}

double f_dx1(double x)
{
    return 2 * x * cos(x) - x * x * sin(x) - 2;
}

double newton1(double x0, double tol, int max_iter)
{
    double x1, error, fx0;
    int iter = 0;

    printf("Iter\tX0\t\tf(x0)\t\tf'(x0)\t\tError\n");
    do
    {
        fx0 = f_new_1(x0);
        double f_dx_x0 = f_dx1(x0);

        if (fabs(f_dx_x0) < 1e-10)
        {
            printf("\nDerivada cerca de cero. No se puede continuar.\n");
            return x0;
        }

        x1 = x0 - fx0 / f_dx_x0;
        error = fabs((x1 - x0) / x1);
        printf("%d\t%.6lf\t%.6lf\t%.6lf\t%.6lf\n", iter, x0, fx0, f_dx_x0, error);

        x0 = x1;
        iter++;

        if (iter >= max_iter)
        {
            printf("\nSe alcanzo el numero maximo de iteraciones.\n");
            return x1;
        }
    } while (error > tol);

    return x1;
}

void p_new_1()
{
    double x0, tol, raiz;
    int max_iter, opcion;

    do
    {
        printf("Ingrese el valor inicial x0: ");
        scanf("%lf", &x0);
        printf("Ingrese la tolerancia: ");
        scanf("%lf", &tol);
        printf("Ingrese el numero maximo de iteraciones: ");
        scanf("%d", &max_iter);

        raiz = newton1(x0, tol, max_iter);
        printf("\nLa raiz aproximada es %.6lf\n", raiz);

        printf("\nDesea encontrar otra raiz? (1 para si, 0 para no): ");
        scanf("%d", &opcion);

    } while (opcion == 1);
}

double f_new_2(double x)
{
    return (6 - (2 / (x * x))) * ((exp(2 + x)) / 4) + 1;
}

double f_dx_2(double x)
{
    return ((exp(2 + x)) * (x + 1) * (3 * x * x - 3 * x + 2)) / (2 * x * x * x);
}

double newton2(double x0, double tol, int max_iter)
{
    double x1, error, fx0;
    int iter = 0;

    printf("Iter\tX0\t\tf(x0)\t\tf'(x0)\t\tError\n");
    do
    {
        fx0 = f_new_2(x0);
        double f_dx_x0 = f_dx_2(x0);

        if (fabs(f_dx_x0) < 1e-10)
        {
            printf("\nDerivada cerca de cero. No se puede continuar.\n");
            return x0;
        }

        x1 = x0 - fx0 / f_dx_x0;
        error = fabs((x1 - x0) / x1);
        printf("%d\t%.6lf\t%.6lf\t%.6lf\t%.6lf\n", iter, x0, fx0, f_dx_x0, error);

        x0 = x1;
        iter++;

        if (iter >= max_iter)
        {
            printf("\nSe alcanzo el numero maximo de iteraciones.\n");
            return x1;
        }
    } while (error > tol);

    return x1;
}

void p_new_2()
{
    double x0, tol, raiz;
    int max_iter, opcion;

    do
    {

        printf("Ingrese el valor inicial x0: ");
        scanf("%lf", &x0);
        printf("Ingrese la tolerancia: ");
        scanf("%lf", &tol);
        printf("Ingrese el numero maximo de iteraciones: ");
        scanf("%d", &max_iter);

        raiz = newton2(x0, tol, max_iter);
        printf("\nLa raiz aproximada es %.6lf\n", raiz);

        printf("\nDesea encontrar otra raiz? (1 para si, 0 para no): ");
        scanf("%d", &opcion);

    } while (opcion == 1);
}

double f_new_3(double x)
{
    return (x * x * x) - (3 * sin(x * x)) + 1;
}

double f_dx3(double x)
{
    return (3 * x * x) - (6 * x * cos(x * x));
}

double newton3(double x0, double tol, int max_iter)
{
    double x1, error, fx0;
    int iter = 0;

    printf("Iter\tX0\t\tf(x0)\t\tf'(x0)\t\tError\n");
    do
    {
        fx0 = f_new_3(x0);
        double f_dx_x0 = f_dx3(x0);

        if (fabs(f_dx_x0) < 1e-10)
        {
            printf("\nDerivada cerca de cero. No se puede continuar.\n");
            return x0;
        }

        x1 = x0 - fx0 / f_dx_x0;
        error = fabs((x1 - x0) / x1);
        printf("%d\t%.6lf\t%.6lf\t%.6lf\t%.6lf\n", iter, x0, fx0, f_dx_x0, error);

        x0 = x1;
        iter++;

        if (iter >= max_iter)
        {
            printf("\nSe alcanzo el numero maximo de iteraciones.\n");
            return x1;
        }
    } while (error > tol);

    return x1;
}

void p_new_3()
{
    double x0, tol, raiz;
    int max_iter, opcion;

    do
    {
		
        printf("Ingrese el valor inicial x0: ");
        scanf("%lf", &x0);
        printf("Ingrese la tolerancia: ");
        scanf("%lf", &tol);
        printf("Ingrese el numero maximo de iteraciones: ");
        scanf("%d", &max_iter);

        raiz = newton3(x0, tol, max_iter);
        printf("\nLa raiz aproximada es %.6lf\n", raiz);

        printf("\nDesea encontrar otra raiz? (1 para si, 0 para no): ");
        scanf("%d", &opcion);

    } while (opcion == 1);
}

double f_new_4(double x)
{
    return (x * x * x) + (6 * (x * x)) + (9.4 * x) + 2.5;
}

double f_dx4(double x)
{
    return (3 * x * x) + (12 * x) + 9.4;
}

double newton4(double x0, double tol, int max_iter)
{
    double x1, error, fx0;
    int iter = 0;

    printf("Iter\tX0\t\tf(x0)\t\tf'(x0)\t\tError\n");
    do
    {
        fx0 = f_new_4(x0);
        double f_dx_x0 = f_dx4(x0);

        if (fabs(f_dx_x0) < 1e-10)
        {
            printf("\nDerivada cerca de cero. No se puede continuar.\n");
            return x0;
        }

        x1 = x0 - fx0 / f_dx_x0;
        error = fabs((x1 - x0) / x1);
        printf("%d\t%.6lf\t%.6lf\t%.6lf\t%.6lf\n", iter, x0, fx0, f_dx_x0, error);

        x0 = x1;
        iter++;

        if (iter >= max_iter)
        {
            printf("\nSe alcanzo el numero maximo de iteraciones.\n");
            return x1;
        }
    } while (error > tol);

    return x1;
}

void p_new_4()
{
    double x0, tol, raiz;
    int max_iter, opcion;

    do
    {
    	
        printf("Ingrese el valor inicial x0: ");
        scanf("%lf", &x0);
        printf("Ingrese la tolerancia: ");
        scanf("%lf", &tol);
        printf("Ingrese el numero maximo de iteraciones: ");
        scanf("%d", &max_iter);

        raiz = newton4(x0, tol, max_iter);
        printf("\nLa raiz aproximada es %.6lf\n", raiz);

        printf("\nDesea encontrar otra raiz? (1 para si, 0 para no): ");
        scanf("%d", &opcion);

    } while (opcion == 1);
}

int main()
{
    caratula();
    int opcion, opcion2, opcion3;

    do
    {
        opcion = menu();
        
        if (opcion != 5)
        {
            opcion2 = menu2();

            if (opcion == 1)
            {
                if (opcion2 == 1)
                {
                    p_secante_1();
                }
                else if (opcion2 == 2)
                {
                    p_new_1();
                }
            }
            else if (opcion == 2)
            {
                if (opcion2 == 1)
                {
                    p_secante_2();
                }
                else if (opcion2 == 2)
                {
                    p_new_2();
                }
            }
            else if (opcion == 3)
            {
                if (opcion2 == 1)
                {
                    p_secante_3();
                }
                else if (opcion2 == 2)
                {
                    p_new_3();
                }
            }
            else if (opcion == 4)
            {
                if (opcion2 == 1)
                {
                    p_secante_4();
                }
                else if (opcion2 == 2)
                {
                    p_new_4();
                }
            }

            printf("Deseas regresar al menu? (si=1 / no=5)\n"); 
            scanf("%d",&opcion);
        }
    } while (opcion==1);

    return 0;
}
