---
title: Operatory binarne
ms.date: 06/14/2018
helpviewer_keywords:
- member-selection operators [C++]
- operators [C++], binary
- binary operators [C++]
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
ms.openlocfilehash: 030ae71fec7a0d1572804f30d09f6f9b2749e436
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181307"
---
# <a name="binary-operators"></a>Operatory binarne

W poniższej tabeli przedstawiono listę operatorów, które mogą być przeciążone.

## <a name="redefinable-binary-operators"></a>Przedefiniowane operatory binarne

|Operator|Name (Nazwa)|
|--------------|----------|
|**,**|Przecinek|
|**!=**|Nierówność|
|**%**|Modulus|
|**%=**|Moduł/przypisanie|
|**&**|Bitowe ORAZ|
|**&&**|Logicznego AND|
|**&=**|Bitowe i/przypisanie|
|**&#42;**|Mnożenie|
|**&#42;=**|Mnożenie/przypisanie|
|**+**|Dodawanie|
|**+=**|Dodawanie/przypisywanie|
|**-**|Odejmowanie|
|**-=**|Odejmowanie/przypisanie|
|**->**|Wybór elementu członkowskiego|
|**->&#42;**|Wybór wskaźnika do elementu członkowskiego|
|**/**|Dzielenie|
|**/=**|Dzielenie/przypisanie|
|**<**|Mniejsze niż|
|**<<**|Przesunięcie w lewo|
|**<<=**|Przesunięcie w lewo/przypisanie|
|**<=**|Mniejsze niż lub równe|
|**=**|Przypisanie|
|**==**|Równości|
|**>**|Większe niż|
|**>=**|Większe niż lub równe|
|**>>**|Przesunięcie w prawo|
|**>>=**|Przesunięcie w prawo/przypisanie|
|**^**|Wyłączny lub|
|**^=**|Wyłączne lub/przypisanie|
|**&#124;**|Bitowe alternatywne OR|
|**&#124;=**|Przypisanie bitowe lub//|
|**&#124;&#124;**|Logicznego OR|

Aby zadeklarować funkcję operatora binarnego jako niestatyczną składową, należy zadeklarować ją w postaci:

> *RET-Type —* **operator** *operacja* **operatora (** *ARG* **)**

gdzie *RET-Type* jest typem zwracanym, *op* jest jednym z operatorów wymienionych w powyższej tabeli *, a argument* jest argumentem dowolnego typu.

Aby zadeklarować funkcję operatora binarnego jako funkcję globalną, należy zadeklarować ją w postaci:

> *RET-Type* **operatora** *op* **(** _arg1_ **,** _arg2_ **)**

gdzie *RET-Type* i *op* są zgodnie z opisem dla funkcji operatora składowych, a *arg1* i *arg2* są argumentami. Co najmniej jeden z argumentów musi być typu klasy.

> [!NOTE]
> Nie ma ograniczeń dla zwracanych typów operatorów binarnych; Jednak większość operatorów binarnych zdefiniowanych przez użytkownika zwraca typ klasy lub odwołanie do typu klasy.

## <a name="see-also"></a>Zobacz też

[Przeładowanie operatora](../cpp/operator-overloading.md)
