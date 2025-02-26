Можете скачать весь проект, но скину код программы на всякий случай
namespace Массивы;

class Program
{
    static void Main(string[] args)
    {
        Console.Write("Введите количество студентов: ");
        int n = int.Parse(Console.ReadLine());

        int[] ocenki = new int[n];

        for (int i = 0; i < n; i++)
        {
            while (true)
            {
                Console.Write($"Введите оценку для студента {i + 1} (от 1 до 5): ");
                int ocenka = int.Parse(Console.ReadLine());

                if (ocenka >= 1 && ocenka <= 5)
                {
                    ocenki[i] = ocenka;
                    break;
                }
                else
                {
                    Console.WriteLine("Ошибка: Оценка должна быть от 1 до 5. Попробуйте снова.");
                }
            }
        }

        double average = CalculateAverage(ocenki);
        Console.WriteLine($"Средний балл студентов: {average:F2}");

        int sdali = SdavshieOcenki(ocenki);
        Console.WriteLine($"Количество сдавших студентов: {sdali}");

        int minOcenka = MinOcenka(ocenki);
        int maxOcenka = MaxOcenka(ocenki);
        Console.WriteLine($"Минимальная оценка: {minOcenka}");
        Console.WriteLine($"Максимальная оценка: {maxOcenka}");
    }

    static double CalculateAverage(int[] ocenki)
    {
        double sum = 0;
        for (int i = 0; i < ocenki.Length; i++)
        {
            sum += ocenki[i];
        }
        return sum / ocenki.Length;
    }

    static int SdavshieOcenki(int[] ocenki)
    {
        int count = 0;
        foreach (int ocenka in ocenki)
        {
            if (ocenka > 4)
            {
                count++;
            }
        }
        return count;
    }

    static int MinOcenka(int[] ocenki)
    {
        int min = ocenki[0];
        foreach (int ocenka in ocenki)
        {
            if (ocenka < min)
            {
                min = ocenka;
            }
        }
        return min;
    }

    static int MaxOcenka(int[] ocenki)
    {
        int max = ocenki[0];
        foreach (int ocenka in ocenki)
        {
            if (ocenka > max)
            {
                max = ocenka;
            }
        }
        return max;
    }
}
