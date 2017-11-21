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
ms.openlocfilehash: c3e907aac68727b752ac0516d2b6fbcbc5d4de84
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [/VD (Wyłącz przemieszczanie konstrukcji)](../../build/reference/vd-disable-construction-displacements.md)