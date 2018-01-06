# comparing-DNA-strands

## 使用hamming distance 來解這個問題
- 可google hamming distance來了解他的定義

## 寫法一(用for來做)
```php
function hammingDistance($strandA, $strandB)
{
    $distance = 0;
    for ($i = 0; $i < strlen($strandA); $i++) {
        $distance += $strandA[$i] === $strandB[$i] ? 0 : 1;
    }

    return $distance;
}
```

## 寫法二(用zip+map+sum來做)
```php
function hammingDistance($strandA, $strandB)
{
    return collect(str_split($strandA))
            ->zip(str_split($strandB))
            ->map(function ($pair) {
                list($a, $b) = $pair;
                return $a === $b ? 0 : 1;
            })->sum();
}
```