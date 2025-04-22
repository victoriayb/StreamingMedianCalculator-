# StreamingMedianCalculator-

import bisect

class StreamingMedianCalculator:
    def __init__(self, initial_values):
        self.nums = sorted(initial_values)

    def add_number_and_return_median(self, i: int) -> float:
        bisect.insort(self.nums, i)  # Efficient sorted insertion

        n = len(self.nums)
        mid = n // 2

        if n % 2 == 1:
            return float(self.nums[mid])
        else:
            return (self.nums[mid - 1] + self.nums[mid]) / 2.0

import pytest
import main

def test_plus_10_returns_15_point_5():
    calc = main.StreamingMedianCalculator([1, 16, 7, 9, 14, 27, 34, 15, 61, 43, 52])
    result = calc.add_number_and_return_median(10)
    assert pytest.approx(result, 0.01) == 15.5

def test_plus_10_then_plus_73_returns_16():
    calc = main.StreamingMedianCalculator([1, 16, 7, 9, 14, 27, 34, 15, 61, 43, 52])
    calc.add_number_and_return_median(10)
    result = calc.add_number_and_return_median(73)
    assert pytest.approx(result, 0.01) == 16

def test_plus_10_then_plus_73_then_plus_100_then_plus_200_returns_27():
    calc = main.StreamingMedianCalculator([1, 16, 7, 9, 14, 27, 34, 15, 61, 43, 52])
    calc.add_number_and_return_median(10)
    calc.add_number_and_return_median(73)
    calc.add_number_and_return_median(100)
    result = calc.add_number_and_return_median(200)
    assert pytest.approx(result, 0.01) == 27
