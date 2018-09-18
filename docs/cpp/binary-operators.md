---
title: Operatory dwuargumentowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- member-selection operators [C++]
- operators [C++], binary
- binary operators [C++]
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c5ad5997657ce9f8a61383a2cd7e685f0a28751
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036556"
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
|**&&**|AND logiczne|
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
|**==**|Równość|
|**>**|Większe niż|
|**>=**|Większe niż lub równe|
|**>>**|Przesunięcie w prawo|
|**>>=**|Przesunięcia w prawo/przypisania|
|**^**|Wykluczające OR|
|**^=**|Wykluczające OR / przydziału|
|**&#124;**|Bitowe alternatywne OR|
|**&#124;=**|Bitowe alternatywne OR / przydziału|
|**&#124;&#124;**|OR logiczne|

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