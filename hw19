#include "rational.h"
#include <iostream>
#include <sstream>
#include <cassert>

struct Treasure {
 public:
  using ValueType = int64_t;

  ValueType gold_;
  ValueType silver_;
  ValueType bronze_;

  Treasure(ValueType gold = 0, ValueType silver = 0, ValueType bronze = 0)
      : gold_(gold), silver_(silver), bronze_(bronze) {}

  Treasure operator+(Treasure rhs) {
    return {gold_ + rhs.gold_, silver_ + rhs.silver_, bronze_ + rhs.bronze_};
  }

  Treasure GetNextDayPrize() {
    return {bronze_ * 2, gold_ + bronze_, silver_ * 2};
  }

  Treasure GetNextDayTreasure() { return *this + GetNextDayPrize(); };

  static Treasure GetNDayTreasure(Treasure treasure, int n) {
    while (n--) {
      treasure = std::move(treasure.GetNextDayTreasure());
    }
    return treasure;
  }

  static Treasure GetNDayTreasureWhithoutPrev(Treasure treasure, int n) {
    while (n--) {
      treasure = std::move(treasure.GetNextDayPrize());
    }
    return treasure;
  }
};

void TestTreasure(int days) {
  auto treasure = Treasure::GetNDayTreasure(Treasure(5), days);
  std::cout << "Treasure on " << days << " day is gold: " << treasure.gold_ << ", silver : " << treasure.silver_
            << ", bronze:" << treasure.bronze_ << std::endl;
}

void TestTreasureWhithoutPrev(int days) {
  auto treasure = Treasure::GetNDayTreasureWhithoutPrev(Treasure(5), days);
  std::cout << "Treasure (WhithoutPrev) on " << days
            << " day is gold: " << treasure.gold_
            << ", silver : " << treasure.silver_
            << ", bronze:" << treasure.bronze_ << std::endl;
}

int main() {
  int n{0};
  while (n++ < 30) {
    TestTreasure(n);
  }

  n = 0;
  while (n++ < 30) {
    TestTreasureWhithoutPrev(n);
  }
}
