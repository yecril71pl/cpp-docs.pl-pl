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
ms.openlocfilehash: 502425728fcd97d2ae8d2efe406dc73370de1272
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="vtordisp"></a>vtordisp
**Określonego języka C++**  
  
 Kontroluje dodanie ukrytego elementu członkowskiego przemieszczenia konstruktora/destruktora vtordisp.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
#pragma vtordisp([push,] n)  
#pragma vtordisp(pop)  
#pragma vtordisp()  
#pragma vtordisp([push,] {on | off})  
```  
  
#### <a name="parameters"></a>Parametry  
 `push`  
 Umieszcza bieżące ustawienie vtordisp w wewnętrznym stosie kompilatora i ustawia nowe ustawienie vtordisp na `n`.  Jeśli nie określono `n`, bieżące ustawienie vtordisp nie zostanie zmienione.  
  
 `pop`  
 Usuwa górny rekord z wewnętrznego stosu kompilatora i przywraca ustawienie vtordisp na usuniętą wartość.  
  
 `n`  
 Określa nową wartość dla ustawienia vtordisp. Możliwe wartości to 0, 1 lub 2, odpowiadające opcjom kompilatora /vd0, /vd1 i /vd2. Aby uzyskać więcej informacji, zobacz [/vd (Wyłącz przemieszczanie konstrukcji)](../build/reference/vd-disable-construction-displacements.md).  
  
 `on`  
 Odpowiednikiem `#pragma vtordisp(1)`.  
  
 `off`  
 Odpowiednikiem `#pragma vtordisp(0)`.  
  
## <a name="remarks"></a>Uwagi  
 Pragma `vtordisp` ma zastosowanie tylko do kodu, który korzysta z baz wirtualnych. Jeśli w klasie pochodnej przeciążono funkcję wirtualną, która jest dziedziczona z wirtualnej klasy bazowej, oraz jeśli konstruktor lub destruktor klasy pochodnej wywoła tę funkcję za pomocą wskaźnika do wirtualnej klasy bazowej, kompilator może wprowadzić dodatkowe ukryte pola `vtordisp` do klas z bazami wirtualnymi.  
  
 Pragma `vtordisp` wpływa na układ klas, które po niej występują. Opcje /vd0, /vd1 i /vd2 określają jednakowe zachowanie dla kompletnych modułów. Określenie `0` lub `off` powoduje pominięcie ukrytych elementów członkowskich `vtordisp`. Wyłącz `vtordisp` tylko jeśli nie istnieje żadna możliwość, aby konstruktory i destruktory klasy wywoływały funkcje wirtualne obiektu wskazywanego przez wskaźnik `this`.  
  
 Określenie `1` lub `on`, domyślnie, włącza ukryte elementy członkowskie `vtordisp`, gdy jest to niezbędne.  
  
 Określanie `2` umożliwia ukrytego `vtordisp` członków dla wszystkich wirtualnych typów podstawowych z funkcji wirtualnych.  `vtordisp(2)` może być konieczne zapewnić prawidłowe działanie `dynamic_cast` na częściowo skonstruowanym obiektem. Aby uzyskać więcej informacji, zobacz [C4436 ostrzeżenie kompilatora (poziom 1)](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md).  
  
 `#pragma vtordisp()` bez argumentów przywraca ustawienie vtordisp do ustawienia początkowego.  
  
```  
#pragma vtordisp(push, 2)  
class GetReal : virtual public VBase { ... };  
#pragma vtordisp(pop)  
```  
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)