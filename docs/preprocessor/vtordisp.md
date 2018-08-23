---
title: vtordisp | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.vtordisp
- vtordisp_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, vtordisp
- vtordisp pragma
ms.assetid: 05b7d73c-43fa-4b62-8c8a-170a9e427391
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5d0b28c855ab8a6f6da814ee17521a5ad7799993
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466124"
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
*push*  
Umieszcza bieżące ustawienie vtordisp na wewnętrznym stosie kompilatora i ustawia nowe ustawienie vtordisp na *n*.  Jeśli *n* nie zostanie określony, bieżące ustawienie vtordisp nie ulega zmianie.  
  
*POP*  
Usuwa górny rekord z wewnętrznego stosu kompilatora i przywraca ustawienie vtordisp na usuniętą wartość.  
  
*N*  
Określa nową wartość dla ustawienia vtordisp. Możliwe wartości to 0, 1 lub 2, odpowiadające `/vd0`, `/vd1`, i `/vd2` opcje kompilatora. Aby uzyskać więcej informacji, zobacz [/vd (Wyłącz przemieszczanie konstrukcji)](../build/reference/vd-disable-construction-displacements.md).  
  
*on*  
Odpowiednikiem `#pragma vtordisp(1)`.  
  
*Wyłączone*  
Odpowiednikiem `#pragma vtordisp(0)`.  
  
## <a name="remarks"></a>Uwagi  
 
**Vtordisp** pragma ma zastosowanie tylko do kodu, który korzysta z baz wirtualnych. Jeśli klasie pochodnej przeciążono funkcję wirtualną, która jest dziedziczona z wirtualnej klasy bazowej, a jeśli Konstruktor lub destruktor klasy pochodnej wywoła tę funkcję za pomocą wskaźnika do wirtualnej klasy bazowej, kompilator może powodować dodatkowych ukrytych **vtordisp** pola do klas z bazami wirtualnymi.  
  
**Vtordisp** pragma wpływa na układ klas, które występują po nim. `/vd0`, `/vd1`, I `/vd2` opcje określają jednakowe zachowanie dla kompletnych modułów. Określanie 0 lub *poza* powoduje pominięcie ukrytych **vtordisp** elementów członkowskich. Wyłącz **vtordisp** tylko w przypadku nie możliwość, że konstruktory i destruktory klasy wywołanie wirtualne funkcje obiektu wskazywanego przez **to** wskaźnika.  
  
Określanie 1 lub *na*, domyślnie, włącza ukryte **vtordisp** elementów członkowskich, gdy jest to konieczne.  
  
Określanie 2 Włącza ukryte **vtordisp** elementów członkowskich dla wszystkich baz wirtualnych z funkcjami wirtualnymi.  `vtordisp(2)` może być konieczne do zapewnienia prawidłowej wydajności **dynamic_cast** na częściowo skonstruowanym obiektem. Aby uzyskać więcej informacji, zobacz [ostrzeżenie kompilatora (poziom 1) C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md).  
  
`#pragma vtordisp()` bez argumentów przywraca ustawienie vtordisp do ustawienia początkowego.  
  
```  
#pragma vtordisp(push, 2)  
class GetReal : virtual public VBase { ... };  
#pragma vtordisp(pop)  
```  
  
**KONIEC określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 
[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)