using System;

namespace ConsoleApp3
{
    internal class Program
    {
        static void Main(string[] args)
        {
            var x0 = 1;
            var y0 = 2;
            var x1 = 3;
            var y1 = 4;
            CheckOutput(x0, y0, x1, y1);   
        }

        public static void CheckOutput(int x0, int  y0, int x1, int y1)
        {
            var dx = Math.Abs(x0 - x1);
            var dy = Math.Abs(y0 - y1);

            Console.WriteLine("Слон: " + GetCheckElephantMove(dx, dy));
            Console.WriteLine("Конь: " + GetCheckHorseMove(dx, dy));
            Console.WriteLine("Ладья: " + GetCheckCastleMove(dx, dy));
            Console.WriteLine("Ферзь: " + GetCheckQueenMove(dx, dy));
            Console.WriteLine("Король: " + GetCheckKingMove(dx, dy));
        }

        private static bool GetCheckElephantMove(int dx, int dy)
        {
            return GetDiagonalCheck(dx, dy);
        }

        private static bool GetCheckHorseMove(int dx, int dy)
        {
            return (dx == 1 && dy == 2) || (dx == 2 && dy == 1);
        }

        private static bool GetCheckCastleMove(int dx, int dy)
        {
            return GetVerticalOrHorizontalCheck(dx, dy);
        }

        private static bool GetCheckQueenMove(int dx, int dy)
        {
            return GetDiagonalCheck(dx, dy) || GetVerticalOrHorizontalCheck(dx, dy);
        }

        private static bool GetCheckKingMove(int dx, int dy)
        {
            return (dx <= 1 && dy <= 1);
        }

        public static bool GetVerticalOrHorizontalCheck(int dx, int dy)
        {
            return (dx == 0 && dy != 0) || (dy == 0 && dx != 0);
        }

        public static bool GetDiagonalCheck(int dx, int dy)
        {
            return (dx == dy && dx != 0);
        }
    }
}

