# task 1 HABR
1.0. Максимальное, минимальное и среднее значение
Задача:
Заполните массив случайным числами и выведите максимальное, минимальное и среднее значение.
Для генерации случайного числа используйте метод Math.random(), который возвращает значение в промежутке [0, 1].
public class Dan{
    public static void main(String[] args) {

        int n = 100;
        double[] array = new double[n];
        for (int i = 0; i < array.length; i++) {
            array[i] = Math.random();
        }

        double max = array[0]; // Массив не должен быть пустым
        double min = array[0];
        double avg = 0;
        for (int i = 0; i < array.length; i++) {
            if(max < array[i])
                max = array[i];
            if(min > array[i])
                min = array[i];
            avg += array[i]/array.length;
        }

        System.out.println("max = " + max);
        System.out.println("min = " + min);
        System.out.println("avg = " + avg);
    }
}
# task 2 HABR
1.2. Поиск простых чисел
Напишите программу, которая выводит на консоль простые числа в промежутке от [2, 100].
Используйте для решения этой задачи оператор "%" (остаток от деления) и циклы.
public class Dan{
    public static void main(String[] args) {
        for (int i = 2; i <= 100; i++) {
            boolean isPrime = true;

            for (int j = 2; j < i; j++) {
                if (i % j == 0) {
                    isPrime = false;
                    break;
                }
            }

            if (isPrime) {
                System.out.println(i);
            }
        }
    }
}
# task 3 HABR
3.1. Найти корень уравнения
Найдите корень уравнения
$cos(x^5) + x^4 - 345.3 * x - 23 = 0$
на отрезке [0; 10] с точностью по x не хуже, чем 0.001. Известно, что на этом промежутке корень единственный.
Используйте для этого метод деления отрезка пополам (и рекурсию).
public class Dan {
    public static double func(double x) {
        return Math.cos(Math.pow(x, 5)) + Math.pow(x, 4) - 345.3 * x - 23;
    }

    // решить уравнение
    public static double solve(double start, double end) {
        if (end - start <= 0.001) {
            return start;
        }

        double x = start + (end - start) / 2;

        if (func(start) * func(x) > 0) {
            return solve(x, end);
        } else {
            return solve(start, x);
        }
    }

    public static void main(String[] args) {
        System.out.println(solve(0, 10));
    }
}
# competition task 2
import java.util.Scanner;

public class lib {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.println("room a, b, h:");
        int a = sc.nextInt();
        int b = sc.nextInt();
        int h = sc.nextInt();

        System.out.println("door w, q:");
        int w = sc.nextInt();
        int q = sc.nextInt();

        System.out.println("window s, p:");
        int s = sc.nextInt();
        int p = sc.nextInt();

        System.out.println("can:");
        int k = sc.nextInt();

        int room = 2 * h * (a + b) - w * q - s * p;

        int can = (room + k - 1) / k;

        System.out.println(can);
    }
}
# competition task 3
import java.util.Scanner;

public class lib {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int L = sc.nextInt();
        int M = sc.nextInt();
        int N = sc.nextInt();

        int fridge = 0, micro = 0, tv = 0;
        double bestf = 0, bestm = 0, bestt = 0;

        for (int i = 1; i <= L; i++) {
            int price = sc.nextInt();
            int discount = sc.nextInt();
            double dprice = price - (price * discount / 100.0);
            if (dprice > bestf) {
                fridge = i;
                bestf = dprice;
            }
        }

        for (int i = 1; i <= M; i++) {
            int price = sc.nextInt();
            int discount = sc.nextInt();
            double discountedPrice = price - (price * discount / 100.0);
            if (discountedPrice > bestm) {
                micro = i;
                bestm = discountedPrice;
            }
        }

        for (int i = 1; i <= N; i++) {
            int price = sc.nextInt();
            int discount = sc.nextInt();
            double discountedPrice = price - (price * discount / 100.0);
            if (discountedPrice > bestt) {
                tv = i;
                bestt = discountedPrice;
            }
        }

        System.out.println(fridge + " " + micro + " " + tv);
    }
}
