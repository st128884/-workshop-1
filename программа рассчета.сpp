#include <iostream>
#include <fstream>
#include <cmath>

int main() {
    std::ifstream f("precise_data.txt");
    if (!f.is_open()) {
        std::cerr << "Ошибка: файл не открыт\n";
        return 1;
    }
    
    const int n = 50;
    double m[n], sum = 0;
    
    for (int i = 0; i < n; i++) {
        f >> m[i];
        sum += m[i];
    }
    f.close();
    
    double mean = sum / n;
    double sum_abs = 0, sum_sq = 0;
    
    for (int i = 0; i < n; i++) {
        double d = m[i] - mean;
        sum_abs += (d < 0) ? -d : d;
        sum_sq += d * d;
    }
    
    double std_dev = sqrt(sum_sq / (n - 1));
    double mean_err = std_dev / sqrt(n);
    
    std::cout.precision(4);
    std::cout << "Сумма: " << sum << "\n";
    std::cout << "Среднее: " << mean << "\n";
    std::cout << "Сумма |di|: " << sum_abs << "\n";
    std::cout << "Сумма di^2: " << sum_sq << "\n";
    std::cout << "σ: " << std_dev << "\n";
    std::cout << "ΔT: " << mean_err << "\n";
    
    return 0;
}
