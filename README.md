def get_max_sum(N, K, A):
    max_sum = 0

    for i in range(N):
        freq = {}
        current_sum = 0
        distinct = 0

        for j in range(i, N):
            val = A[j]
            if val not in freq:
                freq[val] = 1
                distinct += 1
            else:
                freq[val] += 1

            if distinct > K:
                break

            current_sum += val
            max_sum = max(max_sum, current_sum)

    return max_sum