---
title: "Kompilatora (poziom 4) ostrzeżenie C4435 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs: C++
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
caps.latest.revision: "2"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7136cfb61a7452b7e835030216d08f064874df8b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4435"></a>Kompilator C4435 ostrzegawcze (poziom 4)
'klasa1': Układ obiektu pod /vd2 zmieni się ze względu na wirtualną klasę podstawową 'klasa2'  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
 W domyślnym skompilować opcji/vd1, klasa pochodna nie ma `vtordisp` dla wskazanych wirtualnej podstawy pole.  Jeśli/vd2 lub `#pragma vtordisp(2)` , `vtordisp` pole jest obecne, zmiana układu obiektu.  Może to prowadzić do problemów ze zgodnością binarnego, jeśli wchodzącymi w interakcje moduły są kompilowane przy użyciu różnych `vtordisp` ustawienia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4435.  
  
```cpp  
// C4435.cpp  
// compile with: /c /W4  
#pragma warning(default : 4435)  
class A  
{  
public:  
    virtual ~A() {}  
};  
  
class B : public virtual A  // C4435  
{};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [vtordisp](../../preprocessor/vtordisp.md)   
 [/vd (Wyłącz przemieszczanie konstrukcji)](../../build/reference/vd-disable-construction-displacements.md)