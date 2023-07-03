// you can use includes, for example:
// #include <algorithm>

// you can write to stdout for debugging purposes, e.g.
// cout << "this is a debug message" << endl;
// https://codility.com/media/train/solution-flags.pdf

vector<bool> createPeaks(vector<int>& A)
{
    int size = A.size();
    vector<bool> peaks(size, false);
    
    for (int i = 1; i < size - 1; i++)
        if (A[i] > A[i - 1] && A[i] > A[i + 1])
            peaks[i] = true;

    return peaks;
}

// find the first peak located at an index ­>= i.
vector<int> nextPeak(vector<int> &A, vector<bool> &peaks) {
    int size = A.size();
    vector<int> next(size, 0);
    next[size-1] = -1;

    for (int i = size - 2; i >= 0; i--) {
        if (peaks[i])
            next[i] = i;
        else
            next[i] = next[i + 1];
    }
    // cout << "this is a next[i]:" << endl;
    // for (int i = 0; i < size; i++) {
    //     cout << " " << next[i];
    // }
    return next;
}

int solution(vector<int>& A) {
    const int size = A.size();
    if (size <= 2) return 0;

    vector<bool> peaks = createPeaks(A);
    vector<int> next = nextPeak(A, peaks);
    int maxFlags = 0;

    // Let us assume that we have taken i flags. Notice that if we set a flag at position pos then the next flag can only be set in positions ­>= pos + i.
    for (int i = 1; i * (i-1) <= size; i++)
    {
        int numFlags = 0;
        int pos = 0;

        while (pos < size && numFlags < i) {
            pos = next[pos];
            if (pos == -1)   //end
                break;
            pos += i;
            numFlags++;
        }
        maxFlags = max(maxFlags, numFlags);
    }

    return maxFlags;
}
