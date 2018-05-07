---
title: Kompilatora (poziom 1) ostrzeżenie C4251 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4251
dev_langs:
- C++
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 366d66a38685e75e47d8921f9ebd525b334ced7e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4251"></a>Kompilator C4251 ostrzegawcze (poziom 1)
"identyfikator": klasa 'type' musi mieć interfejsu biblioteki dll, który ma być używany przez klientów klasy "type2".  
  
 Aby ograniczyć możliwość uszkodzenie danych podczas eksportowania klasy z [__declspec(dllexport)](../../cpp/dllexport-dllimport.md), upewnij się, że:  
  
-   Wszystkie dane statyczne jest dostęp za pośrednictwem funkcji, które są eksportowane z biblioteki DLL.  
  
-   Nie została wbudowana metod klasy można modyfikować danych statycznych.  
  
-   Nie została wbudowana metod klasy należy użyć funkcji CRT lub innych funkcji biblioteki dane statyczne (zobacz [potencjalne błędy przekazywanie CRT obiektów między granic DLL](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md) Aby uzyskać więcej informacji).  
  
-   Nie metody klasy (niezależnie od tego ze śródwierszowaniem) można używać typów, których wystąpienia EXE i DLL różnią się w sposób danych statycznych.  
  
 Można uniknąć, eksportowanie klas przez definiowanie przez bibliotekę DLL, która definiuje klasę z funkcji wirtualnych i zostanie funkcje można wywołać w celu utworzenia wystąpienia i usuwania obiektów tego typu.  Następnie można po prostu Wywołaj funkcje wirtualne w typie.  
  
 Aby uzyskać więcej informacji o eksportowaniu szablonów, zobacz [ http://support.microsoft.com/default.aspx?scid=KB; EN-US; 168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958).  
  
 C4251 można zignorować, jeśli są pochodny typ w standardowa biblioteka C++, kompilowanie zlecenia debug (**/MTd**) i których dotyczy _Container_base komunikat o błędzie kompilatora.  
  
```  
// C4251.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251  
```