---
title: Kompilatora (poziom 4) ostrzeżenie C4121 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4121
dev_langs:
- C++
helpviewer_keywords:
- C4121
ms.assetid: 8c5b85c9-2543-426b-88bc-319c50158c7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c1cda66d120278034fc8c19ba0221be047a75eb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293290"
---
# <a name="compiler-warning-level-4-c4121"></a>Kompilator C4121 ostrzegawcze (poziom 4)
'symbol' : wyrównanie elementu członkowskiego było wrażliwe na pakowanie  
  
 Kompilator dodał dopełnienie, aby wyrównać element członkowski struktury na granicy pakowania, ale wartość pakowania jest mniejsza niż rozmiar tego elementu. Na przykład poniższy fragment kodu powoduje C4121:  
  
```  
// C4121.cpp  
// compile with: /W4 /c  
#pragma pack(2)  
struct s  
{  
   char a;  
   int b; // C4121  
   long long c;  
};  
```  
  
 Aby rozwiązać ten problem, wprowadź jedną z następujących zmian:  
  
-   Zmień rozmiar pakowania na rozmiar elementu członkowskiego, który spowodował ostrzeżenie, lub większy rozmiar. Na przykład, w tym fragmencie, należy zmienić `pack(2)` do `pack(4)` lub `pack(8)`.  
  
-   Zmień kolejność deklaracji elementów członkowskich według rozmiarów, od największych do najmniejszych. We fragmencie, odwrócić kolejność elementów członkowskich struktury tak, aby `long long` poprzedza element członkowski `int`i `int` poprzedza `char`.  
  
 To ostrzeżenie występuje tylko, gdy kompilator dodaje dopełnienie przed elementami członkowskimi. Nie następuje, gdy pakowanie umieściło dane w lokalizacji w pamięci, która nie jest dostosowana dla tego typu danych, ale nie umieszczono dopełnienia przed elementem członkowskim. Gdy dane nie są wyrównane na granicach, które stanowią wielokrotność rozmiaru danych, sprawność działania może się zmniejszyć. Odczytywanie i zapisywanie niewyrównanych danych powoduje usterki procesora w niektórych architekturach, a znalezienie i usunięcie problemów może zająć czas dwa, a nawet trzy rzędy wielkości dłuższy niż normalnie. Dostępów do niewyrównanych danych nie można przenieść na niektóre architektury RISC.  
  
 Można użyć [#pragma pack](../../preprocessor/pack.md) lub [/Zp](../../build/reference/zp-struct-member-alignment.md) określone wyrównanie struktury. (Kompilator nie generuje tego ostrzeżenia, kiedy **/Zp1** jest określona.)