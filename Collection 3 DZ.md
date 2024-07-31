static int HasExit(int startI, int startJ, int[,] l)
{
    bool[,] visited = new bool[l.GetLength(0), l.GetLength(1)];
    Queue<int[]> queue = new Queue<int[]>();

    queue.Enqueue(new int[] { startI, startJ });

    visited[startI, startJ] = true;

    while (queue.Count > 0)
    {
        int[] point = queue.Dequeue();
        int i = point[0];
        int j = point[1];

        if (i == 0 || i == l.GetLength(0) - 1 || j == 0 || j == l.GetLength(1) - 1)
        {
            return 1; // находим выход
        }

        for (int dx = -1; dx <= 1; dx++)
        {
            for (int dy = -1; dy <= 1; dy++)
            {
                int ni = i + dx;
                int nj = j + dy;

                if (ni >= 0 && ni < l.GetLength(0) && nj >= 0 && nj < l.GetLength(1) && !visited[ni, nj] && l[ni, nj] == 1)
                {
                    queue.Enqueue(new int[] { ni, nj });
                    visited[ni, nj] = true;
                }
            }
        }
    }

    return 0; // не находим



