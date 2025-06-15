
from collections import defaultdict

def get_max_sum(N, K, A):
    max_sum = 0
    current_sum = 0
    left = 0
    freq = defaultdict(int)
    distinct = 0

    for right in range(N):
        val = A[right]
        freq[val] += 1

        if freq[val] == 1:  # First time seeing this element
            distinct += 1

        current_sum += val

        # Shrink window from left if distinct count > K
        while distinct > K:
            freq[A[left]] -= 1
            current_sum -= A[left]

            if freq[A[left]] == 0:
                distinct -= 1

            left += 1

        # Update max sum for valid subarray
        max_sum = max(max_sum, current_sum)

    return max_sum