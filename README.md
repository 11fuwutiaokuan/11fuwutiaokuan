import random

def generate_unequal_shares(total, num_shares, max_share):
    shares = []
    remaining = total
    for _ in range(num_shares):
        if remaining / (num_shares - len(shares)) > max_share:
            max_possible_share = min(max_share, remaining / (num_shares - len(shares)))
        else:
            max_possible_share = remaining / (num_shares - len(shares))
        share = random.uniform(1, max_possible_share)  # 使用均匀分布生成随机数，但也可以尝试其他分布
        shares.append(round(share, 4))  # 四舍五入到小数点后四位
        remaining -= share
    return shares

total = 5272.2702
num_shares = 90
max_share = 300

shares = generate_unequal_shares(total, num_shares, max_share)
print(shares)
