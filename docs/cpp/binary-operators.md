---
title: Operatory binarne
ms.date: 06/14/2018
helpviewer_keywords:
- member-selection operators [C++]
- operators [C++], binary
- binary operators [C++]
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
ms.openlocfilehash: 700d8fd784862c3e9f81fcde839063ff0a4696bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176658"
---
# <a name="binary-operators"></a>Operatory binarne

W poniższej tabeli przedstawiono listę operatorów, które mogą być przeciążone.

## <a name="redefinable-binary-operators"></a>Operatory dwuargumentowe które można definiować ponownie

|Operator|Nazwa|
|--------------|----------|
|**,**|Przecinek|
|**\!=**|Nierówność|
|**%**|Modulo|
|**%=**|Modulo i i przypisanie|
|**&**|Bitowe ORAZ|
|**&&**|Logicznego AND|
|**&=**|Bitowe AND / przydziału|
|**&#42;**|Mnożenie|
|**&#42;=**|Mnożenie i przypisanie|
|**+**|Dodawanie|
|**+=**|Dodawanie i przypisanie|
|**-**|Odejmowanie|
|**-=**|Odejmowanie i przypisanie|
|**->**|Wybór elementu członkowskiego|
|**->&#42;**|Wybór wskaźników do elementów członkowskich|
|**/**|Dzielenie|
|**/=**|Dzielenie i przypisanie|
|**<**|Mniejsze niż|
|**<<**|Przesunięcie w lewo|
|**<<=**|Lewy shift/przypisania|
|**<=**|Mniejsze niż lub równe|
|**=**|Przypisanie|
|**==**|Równości|
|**>**|Większe niż|
|**>=**|Większe niż lub równe|
|**>>**|Przesunięcie w prawo|
|**>>=**|Przesunięcia w prawo/przypisania|
|**^**|Wykluczające OR|
|**^=**|Wykluczające OR / przydziału|
|**&#124;**|Bitowe alternatywne OR|
|**&#124;=**|Bitowe alternatywne OR / przydziału|
|**&#124;&#124;**|Logicznego OR|

Aby zadeklarować funkcję operatora binarnego jako niestatyczny element członkowski, należy zadeklarować ją w postaci:

> *RET-type* **operator** *op* **(** *arg* **)**

gdzie *ret-type* jest typem zwracanym *op* jest jednym z operatorów wymienionych w powyższej tabeli i *arg* jest argumentem typu.

Aby zadeklarować funkcję operatora binarnego jako funkcję globalną, należy zadeklarować ją w postaci:

> *RET-type* **operator** *op* **(** _arg1_**,** _argument2_ **)**

gdzie *ret-type* i *op* są opisane dla funkcji operatora składowej i *arg1* i *argument2* argumentów. Co najmniej jeden z argumentów musi być typem klasy.

> [!NOTE]
> Nie ma żadnych ograniczeń względem typów zwracanych operatorów binarnych; Jednak większość zdefiniowanych przez użytkownika operatory dwuargumentowe Zwróć odwołanie do typu klasy lub typu klasy.

## <a name="see-also"></a>Zobacz także

[Przeładowanie operatora](../cpp/operator-overloading.md)