---
title: Kompilatora (poziom 2) ostrzeżenie C4275 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4275
dev_langs:
- C++
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5d2a3cd7c4b937f8bee1b8f8e37e0619cc224ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292074"
---
# <a name="compiler-warning-level-2-c4275"></a>Kompilator C4275 ostrzegawcze (poziom 2)
nie - classkey interfejsu biblioteki DLL 'Identyfikator' używany jako bazowy DL classkey interfejsu biblioteki DLL 'Identyfikator'  
  
 Wyeksportowanej klasy pochodzi z klasy, które nie zostały wyeksportowane.  
  
 Aby ograniczyć możliwość uszkodzenie danych podczas eksportowania klasy z [__declspec(dllexport)](../../cpp/dllexport-dllimport.md), upewnij się, że:  
  
-   Wszystkie dane statyczne jest dostępny za pośrednictwem funkcji, które są eksportowane z biblioteki DLL.  
  
-   Nie została wbudowana metod klasy można modyfikować danych statycznych.  
  
-   Nie została wbudowana metod klasy funkcji CRT lub innych funkcji biblioteki użyć danych statycznych.  
  
-   Żadnych funkcji śródwierszowych klasy używać funkcji CRT lub innych funkcji biblioteki, where, na przykład uzyskujesz dostęp do statycznych danych.  
  
-   Nie metody klasy (niezależnie od tego ze śródwierszowaniem) można używać typów, których wystąpienia EXE i DLL różnią się w sposób danych statycznych.  
  
 Można uniknąć, eksportowanie klas przez definiowanie przez bibliotekę DLL, która definiuje klasę z funkcji wirtualnych i zostanie funkcje można wywołać w celu utworzenia wystąpienia i usuwania obiektów tego typu.  Następnie można po prostu Wywołaj funkcje wirtualne w typie.  
  
 Aby uzyskać więcej informacji o eksportowaniu szablonów, zobacz [ http://support.microsoft.com/default.aspx?scid=KB; EN-US; 168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958).  
  
 C4275 można zignorować w programie Visual C++, jeśli są pochodny typ w standardowa biblioteka C++, kompilowanie zlecenia debug (**/MTd**) i których dotyczy _Container_base komunikat o błędzie kompilatora.  
  
```  
// C4275.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275  
```