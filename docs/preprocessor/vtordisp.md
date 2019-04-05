---
title: vtordisp
ms.date: 10/18/2018
f1_keywords:
- vc-pragma.vtordisp
- vtordisp_CPP
helpviewer_keywords:
- pragmas, vtordisp
- vtordisp pragma
ms.assetid: 05b7d73c-43fa-4b62-8c8a-170a9e427391
ms.openlocfilehash: 67c6c329bcee75012f6075334760925eca945501
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034381"
---
# <a name="vtordisp"></a>vtordisp

**Określonego język C++**

Kontroluje dodanie ukrytego elementu członkowskiego przemieszczenia konstruktora/destruktora vtordisp.

## <a name="syntax"></a>Składnia

```cpp
#pragma vtordisp([push,] n)
#pragma vtordisp(pop)
#pragma vtordisp()
#pragma vtordisp([push,] {on | off})
```

### <a name="parameters"></a>Parametry

*wypychania*<br/>
Umieszcza bieżące ustawienie vtordisp na wewnętrznym stosie kompilatora i ustawia nowe ustawienie vtordisp na *n*.  Jeśli *n* nie zostanie określony, bieżące ustawienie vtordisp nie ulega zmianie.

*POP*<br/>
Usuwa górny rekord z wewnętrznego stosu kompilatora i przywraca ustawienie vtordisp na usuniętą wartość.

*n*<br/>
Określa nową wartość dla ustawienia vtordisp. Możliwe wartości to 0, 1 lub 2, odpowiadające `/vd0`, `/vd1`, i `/vd2` opcje kompilatora. Aby uzyskać więcej informacji, zobacz [/vd (Wyłącz przemieszczanie konstrukcji)](../build/reference/vd-disable-construction-displacements.md).

*on*<br/>
Odpowiednikiem `#pragma vtordisp(1)`.

*wyłączone*<br/>
Odpowiednikiem `#pragma vtordisp(0)`.

## <a name="remarks"></a>Uwagi

**Vtordisp** pragma ma zastosowanie tylko do kodu, który korzysta z baz wirtualnych. Jeśli klasie pochodnej przeciążono funkcję wirtualną, która jest dziedziczona z wirtualnej klasy bazowej, a jeśli Konstruktor lub destruktor klasy pochodnej wywoła tę funkcję za pomocą wskaźnika do wirtualnej klasy bazowej, kompilator może powodować dodatkowych ukrytych **vtordisp** pola do klas z bazami wirtualnymi.

**Vtordisp** pragma wpływa na układ klas, które występują po nim. `/vd0`, `/vd1`, I `/vd2` opcje określają jednakowe zachowanie dla kompletnych modułów. Określanie 0 lub *poza* powoduje pominięcie ukrytych **vtordisp** elementów członkowskich. Wyłącz **vtordisp** tylko w przypadku nie możliwość, że konstruktory i destruktory klasy wywołanie wirtualne funkcje obiektu wskazywanego przez **to** wskaźnika.

Określanie 1 lub *na*, domyślnie, włącza ukryte **vtordisp** elementów członkowskich, gdy jest to konieczne.

Określanie 2 Włącza ukryte **vtordisp** elementów członkowskich dla wszystkich baz wirtualnych z funkcjami wirtualnymi.  `vtordisp(2)` może być konieczne do zapewnienia prawidłowej wydajności **dynamic_cast** na częściowo skonstruowanym obiektem. Aby uzyskać więcej informacji, zobacz [ostrzeżenie kompilatora (poziom 1) C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md).

`#pragma vtordisp()`, bez argumentów przywraca ustawienie vtordisp do ustawienia początkowego.

```cpp
#pragma vtordisp(push, 2)
class GetReal : virtual public VBase { ... };
#pragma vtordisp(pop)
```

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)