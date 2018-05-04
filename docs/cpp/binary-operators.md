---
title: Operatory binarne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 3b930c548ea411beb03255d694f2423903053288
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="binary-operators"></a>Operatory binarne
W poniższej tabeli przedstawiono listę podmiotów, które mogą być przeciążone.  
  
### <a name="redefinable-binary-operators"></a>Operatory binarne które można definiować ponownie  
  
|Operator|Nazwa|  
|--------------|----------|  
|**,**|Przecinek|  
|`!=`|Nierówność|  
|`%`|Modulo|  
|`%=`|Moduł/przypisania|  
|**&**|Bitowe ORAZ|  
|**&&**|AND logiczne|  
|**&=**|Iloczynu bitowego AND / przypisania|  
|**\***|Mnożenie|  
|**\*=**|Przypisanie/mnożenia|  
|**+**|Dodawanie|  
|`+=`|Dodanie/przypisania|  
|**-**|Odejmowanie|  
|**-=**|Przypisanie odejmowania /|  
|**->**|Wybór elementu członkowskiego|  
|**->\***|Wybór wskaźnika do elementu członkowskiego|  
|**/**|Dzielenie|  
|`/=`|Dzielenie/przypisania|  
|**<**|Mniejsze niż|  
|**<<**|Przesunięcie w lewo|  
|**<<=**|Po lewej stronie przypisania przesunięcia /|  
|**<=**|Mniejsze niż lub równe|  
|**=**|Przypisanie|  
|`==`|Równość|  
|**>**|Większe niż|  
|**>=**|Większe niż lub równe|  
|**>>**|Przesunięcie w prawo|  
|**>>=**|Przypisania/przesunięcia w prawo|  
|**^**|Wyłączny OR|  
|`^=`|Wyłączny OR / przypisania|  
|**&#124;**|Bitowe alternatywne OR|  
|`&#124;=`|Operator włącznie lub / przypisania|  
|`&#124;&#124;`|OR logiczne|  
  
 Do zadeklarowania funkcji operatora binarnego jako niestatycznego elementu członkowskiego, muszą deklarować go w postaci:  
  
 *Typ RET* **operator**`op`**(** `arg` **)**  
  
 gdzie *ret typu* jest zwracany typ `op` jest jednym z podmiotów wymienione w powyższej tabeli i `arg` jest argumentem typu.  
  
 Do zadeklarowania funkcji operatora binarnego jako funkcję globalną, muszą deklarować go w postaci:  
  
 *Typ RET* **operator**`op`**(** `arg1` **,** `arg2` **)**  
  
 gdzie *ret typu* i `op` są zgodnie z opisem dla funkcji Członkowskich operatora i `arg1` i `arg2` argumentów. Co najmniej jeden z argumentów musi być typu klasy.  
  
> [!NOTE]
>  Nie podlega ograniczeniom typ zwracany operatorów binarnych; Jednak większość zdefiniowane przez użytkownika operatory binarne zwracać typu klasy lub odwołanie do typu klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Przeładowanie operatora](../cpp/operator-overloading.md)