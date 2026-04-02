DP 答题卡

1.  线性问题【最少个数，方案数，是否可行，最大价值
    答题思路：1. 先看 dp[i] 表示什么 2. 看 base case：
    最少个数： dp[0] = 0;【因为凑出 0 不需要任何元素。】
    dp[0] = 1;【因为凑出 0 有 1 种方式：什么都不选。】3. 想“最后一步”
    最少个数：最后放一个数 x”，那前面就得先凑出 i - x
    可行性类： dp[i] = dp[i] || dp[i - x] 4. 判断是完全背包还是 0/1 背包
    完全背包：
    Coin Change
    Perfect Squares
    Combination Sum

            不完全背包：
            Partition Equal Subset Sum
            Target Sum（转换后）
            Last Stone Weight II

答题模版：
最少个数：【279 Perfect Squares， 322 Coin Change】
public int solve(int[] nums, int target) {
int[] dp = new int[target + 1];
Arrays.fill(dp, target + 1); // INF
dp[0] = 0;

        for (int i = 1; i <= target; i++) {
            for (int x : nums) {    //
                if (i >= x) {
                    dp[i] = Math.min(dp[i], dp[i - x] + 1);
                }
            }
        }

        return dp[target] == target + 1 ? -1 : dp[target];
    }

变种问题：
代表题 3：518. Coin Change II
代表题 5：416. Partition Equal Subset Sum
代表题 6：139. Word Break
