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
