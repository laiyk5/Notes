Best strategy: You can use iPhone with 2700 RMB/iPhone and change for a better one every 2 years!

策略就是保持落后两代，两年一换，每次都买pro机型的第二档存储
实操就是买99新二手，贴膜带套换官方电池好好保养，过两年当99新卖掉，再换新的落后两代的二手
结果就是省70%+，2700爽用iPhone

## Naive Strategy

buy newest model Pro with second level storage from apple store with full price, and ignore damage risk.

### Real Data Example

iPhone 14 Pro purchased at 2023.3.16

- buying costs: 8899
- fix screen: 280
- fix motherboard: 500
- fix battery, camera: 500
- Phone case, screen protector: 100

assume the life cycle is around 4 years, then the total cost is: $9899+380 = 10279$
cost/day = $10279 / (4 \* 365) \approx 7.0404109589$

## Smart Strategy

best iPhone purchasing strategy

2-Gens late, second handed, change every two years.

### Simulation Settings

- current strategy:
  - Naive(history): change every 4 years, brand new, latest, second level storage:
    - per day: $7.0404109589$,
    - total: 10279 RMB
  - Continued(if continue with this plan):
    - iPhone 17 Pro 512G: 10999
    - Accessories costs:
      - phone case + screen protector (4 years): 160
- smart strategy:
  - buy iPhone 15 Pro 256G (Second Handed): 3920 RMB
  - sell iPhone 13 Pro 256G (Second Handed): 2100 RMB
  - difference: 1820 RMB
    - Accessories costs:
      - (Phone case + screen protector) \* 2: 160 RMB
      - potential battery costs (official): 809 RMB

way more cheaper!!!!

### Simulation Results

📱 Naive Strategy
Phone cost:     ¥8,899.00
Repair costs:   ¥1,280.00
Accessories:    ¥100.00
─────────────────────────────
TOTAL:          ¥10,279.00
Per day:        ¥7.0404
Per year:       ¥2,569.75

📱 Current Plan (Continued)
Phone cost:     ¥10,999.00
Repair costs:   ¥969.00
Accessories:    ¥160.00
─────────────────────────────
TOTAL:          ¥12,128.00
Per day:        ¥8.3068
Per year:       ¥3,032.00

📱 Smart Strategy (2-year view)
Phone cost:     ¥1,820.00
Repair costs:   ¥809.00
Accessories:    ¥160.00
─────────────────────────────
TOTAL:          ¥2,789.00
Per day:        ¥3.8205
Per year:       ¥1,394.50

### Comparison

💰 Smart vs Naive:
Daily savings:  ¥3.2199
4-year savings: ¥4,701.00 (45.7%)

💰 Smart vs Current Plan:
Daily savings:  ¥4.4863
4-year savings: ¥6,550.00 (54.0%)

## Appendix: Simulation Code

```run-python
import pandas as pd
from dataclasses import dataclass

SMARTSTR_NEW_PHONE_PRICE = 3920
SMARTSTR_OLD_PHONE_PRICE = 2100

@dataclass
class Strategy:
    name: str
    phone_cost: float
    repair_costs: float
    accessories_cost: float
    lifecycle_years: float
    description: str

    def total_cost(self) -> float:
        return self.phone_cost + self.repair_costs + self.accessories_cost
    
    def cost_per_day(self) -> float:
        return self.total_cost() / (self.lifecycle_years * 365)
    
    def cost_per_year(self) -> float:
        return self.cost_per_day() * 365

def calculate_strategies():
    # Strategy 1: Naive - Buy newest Pro, full price, 4 year lifecycle
    naive = Strategy(
        name="Naive Strategy",
        phone_cost=8899,
        repair_costs=280 + 500 + 500,  # screen + motherboard + battery/camera
        accessories_cost=100,
        lifecycle_years=4,
        description="Buy newest Pro model, full price, keep 4 years"
    )
    
    # Strategy 2: Current Plan Continuation (extrapolated)
    current_plan = Strategy(
        name="Current Plan (Continued)",
        phone_cost=10999,  # iPhone 17 Pro 512GB
        repair_costs=969,
        accessories_cost=160,
        lifecycle_years=4,
        description="Continue current pattern: latest model, 4 years"
    )
    
    # Strategy 3: Smart - 2-gen late, second hand, 2-year cycles
    # Two cycles over 4 years: iPhone 13 Pro (2100) → iPhone 15 Pro (3920)
    smart_2yr = Strategy(
        name="Smart Strategy (2-year view)",
        phone_cost=(SMARTSTR_NEW_PHONE_PRICE-SMARTSTR_OLD_PHONE_PRICE),
        repair_costs=809,     # one battery replacement
        accessories_cost=160,  # 2 sets of accessories
        lifecycle_years=2,
        description="2-gen late, second hand, swap every 2 years"
    )
    
    return naive, current_plan, smart_2yr

def print_comparison():
    naive, current, smart = calculate_strategies()
    strategies = [naive, current, smart]
    
    print("=" * 80)
    print("iPhone Purchasing Strategy Comparison")
    print("=" * 80)
    
    for s in strategies:
        print(f"\n📱 {s.name}")
        print(f"   Phone cost:     ¥{s.phone_cost:,.2f}")
        print(f"   Repair costs:   ¥{s.repair_costs:,.2f}")
        print(f"   Accessories:    ¥{s.accessories_cost:,.2f}")
        print(f"   ─────────────────────────────")
        print(f"   TOTAL:          ¥{s.total_cost():,.2f}")
        print(f"   Per day:        ¥{s.cost_per_day():.4f}")
        print(f"   Per year:       ¥{s.cost_per_year():,.2f}")
    
    # Savings analysis
    print("\n" + "=" * 80)
    print("SAVINGS ANALYSIS")
    print("=" * 80)
    
    # vs Naive
    save_naive = (naive.cost_per_year() - smart.cost_per_year()) * naive.lifecycle_years
    print(f"\n💰 Smart vs Naive:")
    print(f"   Daily savings:  ¥{naive.cost_per_day() - smart.cost_per_day():.4f}")
    print(f"   4-year savings: ¥{save_naive:,.2f} ({save_naive/naive.total_cost()*100:.1f}%)")
    
    # vs Current
    save_current = (current.cost_per_year() - smart.cost_per_year()) * current.lifecycle_years
    print(f"\n💰 Smart vs Current Plan:")
    print(f"   Daily savings:  ¥{current.cost_per_day() - smart.cost_per_day():.4f}")
    print(f"   4-year savings: ¥{save_current:,.2f} ({save_current/current.total_cost()*100:.1f}%)")

    return strategies

strategies = print_comparison()
```
