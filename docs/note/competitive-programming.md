# Competitive Programming
- 切り上げ
```
double x = 3.2;
cout << ceil(x) << endl;

[Output]
4
```

- 出力の桁数指定
    - `#include <iomanip>`
```
double ans = 1.322;
cout << setprecision(2) << ans << endl;

[Output]
1.32
```