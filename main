#include <iostream>
#include <vector>
#include <cstdlib>
#include <ctime>
#include <cmath>
 
typedef unsigned long long num_type;
 
bool is_prime(num_type number)
{
    if (number < 2)
        return false;
 
    if (number == 2)
        return true;
 
    for (num_type div = static_cast<num_type>(sqrt(static_cast<double>(number))) + 1;
         div >= 2;
         --div)
        if (number % div == 0)
            return false;
 
    return true;
}
 
void random_init()
{
    srand(static_cast<unsigned>(time(0)));
}
 
num_type random(num_type lower_bound, num_type upper_bound)
{
    return lower_bound + (upper_bound - lower_bound) * static_cast<num_type>(rand()) / RAND_MAX;
}
 
typedef std::vector<num_type> row_type;
typedef std::vector<row_type> matrix_type;
 
matrix_type generate_matrix(size_t rows, size_t cols)
{
    matrix_type matrix(rows, row_type(cols, 0));
 
    for (size_t i = 0; i < rows; ++i)
        for (size_t j = 0; j < cols; ++j)
            matrix[i][j] = random(0, 10000);
 
    return matrix;
}
 
void print_matrix(const matrix_type& matrix)
{
    for (size_t i = 0; i < matrix.size(); ++i)
    {
        for (size_t j = 0; j < matrix[i].size(); ++j)
            std::cout << matrix[i][j] << "  ";
 
        std::cout << std::endl;
    }
}
 
int main()
{
    random_init();
 
    matrix_type matrix = generate_matrix(5, 5);
 
    print_matrix(matrix);
 
    size_t prime_count = 0;
 
    for (size_t i = 0; i < matrix.size(); ++i)
    {
        for (size_t j = 0; j < matrix[i].size(); ++j)
        {
            if (is_prime(matrix[i][j]))
            {
                ++prime_count;
 
                std::cout << "Prime[" << prime_count << "] = " << matrix[i][j] << std::endl;
            }
        }
    }
 
    std::cout << "Number of primes in matrix: " << prime_count << std::endl;
 
    return 0;
}
