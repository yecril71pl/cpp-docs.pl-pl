---
title: pakiet | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- pack_CPP
- vc-pragma.pack
dev_langs: C++
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1bf4c7a67abe03a1138eb2eb016426675c20355c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="pack"></a>pakiet
Określa sposób wyrównania pakowania struktury, Unii i elementów członkowskich klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )  
```  
  
## <a name="remarks"></a>Uwagi  
 Do klasy pakietu jest umieszczenie jej elementów członkowskich bezpośrednio po sobie nawzajem w pamięci, co może oznaczać, że niektóre lub wszystkie elementy Członkowskie może być wyrównany na granicy mniejszą niż domyślne wyrównanie architektury docelowej. `pack`Umożliwia sterowanie na poziomie deklaracja danych. Ta różni się od — opcja kompilatora [/Zp](../build/reference/zp-struct-member-alignment.md), który tylko można kontrolować poziom modułu. `pack`działa na pierwszym `struct`, `union`, lub `class` deklaracji po pragma jest widoczna. `pack`nie ma wpływu na definicje. Wywoływanie `pack` z zestawami nie argumentów `n` jest wartość określona w opcji kompilatora **/Zp**. Jeśli nie ustawiono opcję kompilatora, wartość domyślna to 8.  
  
 Jeśli zmienisz wyrównania struktury, nie można używać jak dużo miejsca w pamięci, ale może wyświetlić spadek wydajności lub nawet uzyskać wyjątek wygenerowany sprzętu dla niewyrównany dostęp.  To zachowanie wyjątek można zmienić za pomocą [SetErrorMode](http://msdn.microsoft.com/library/windows/desktop/ms680621).  
  
 **Pokaż** (opcjonalnie)  
 Wyświetla bieżącą wartość bajtu wyrównania pakowania. Wartość jest wyświetlana przez komunikat ostrzegawczy.  
  
 **wypychania** (opcjonalnie)  
 Wypchnięcia bieżącego wyrównania pakowania wartość wewnętrznego stosu kompilatora i ustawia wartość bieżącego wyrównania pakowania do `n`. Jeśli `n` nie zostanie określony, bieżącą wartość wyrównania pakowania jest naciśnięty.  
  
 **POP** (opcjonalnie)  
 Usuwa rekord z góry stosu wewnętrznego kompilatora. Jeśli `n` nie zostanie określony z **pop**, wartość pakowania skojarzony z rekordem wynikowy wierzchołku stosu jest nowa wartość wyrównania pakowania. Jeśli `n` jest określony, na przykład `#pragma pack(pop, 16)`, `n` staje się nowa wartość wyrównania pakowania. Jeśli pop z `identifier`, na przykład `#pragma pack(pop, r1)`, a następnie wszystkie rekordy na stosie są zdjęte ze stosu do rekordu, który ma `identifier` został znaleziony. Czy zdjęte ze stosu rekordu i wartość pakowania skojarzony z rekordem wynikowy na wierzchu z jest stos nowe pakowania wartość wyrównania. Jeśli pop z `identifier` nie znaleziono żadnych rekordów na stosie, a następnie **pop** jest ignorowana.  
  
 `identifier`(opcjonalnie)  
 W przypadku użycia z **wypychania**, przypisuje nazwę w rekordzie na stosie wewnętrznych kompilatora. W przypadku użycia z **pop**, POP rejestruje wewnętrzny stosu do `identifier` zostanie usunięta; Jeśli `identifier` nie znaleziono na stosie wewnętrznego, nic nie jest zdjęte ze stosu.  
  
 `n`(opcjonalnie)  
 Określa wartość, w bajtach, służący do dokumentu. Jeśli opcja kompilatora [/Zp](../build/reference/zp-struct-member-alignment.md) nie jest ustawiony dla modułu, wartością domyślną dla `n` jest 8. Prawidłowe wartości to 1, 2, 4, 8 do 16. Wyrównanie elementu członkowskiego będzie w granicach jest wielokrotnością liczby `n` lub wielokrotnością rozmiaru elementu członkowskiego, w zależności od jest mniejsza.  
  
 `#pragma pack(pop, identifier, n)`nie jest zdefiniowana.  
  
 Aby uzyskać więcej informacji na temat sposobu modyfikowania wyrównania zobacz następujące tematy:  
  
-   [__alignof](../cpp/alignof-operator.md)  
  
-   [Dopasuj](../cpp/align-cpp.md)  
  
-   [__unaligned](../cpp/unaligned.md)  
  
-   [Przykłady wyrównania struktury](../build/examples-of-structure-alignment.md) (x64 określonych)  
  
    > [!WARNING]
    >  Należy pamiętać, że w programie Visual Studio 2015 i nowszych można użyć operatory alignof i alignas standardowe którego, w przeciwieństwie do `__alignof` i `declspec( align )` można przenosić między kompilatory. C++ standard nie dotyczy pakowania, więc należy nadal używać `pack` (lub odpowiedniego rozszerzenia na inne kompilatory) do określenia wyrównania jest mniejszy niż rozmiar słowa architektury docelowej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób użycia `pack` pragma, aby zmienić wyrównania struktury.  
  
```  
// pragma_directives_pack.cpp  
#include <stddef.h>  
#include <stdio.h>  
  
struct S {  
   int i;   // size 4  
   short j;   // size 2  
   double k;   // size 8  
};  
  
#pragma pack(2)  
struct T {  
   int i;  
   short j;  
   double k;  
};  
  
int main() {  
   printf("%zu ", offsetof(S, i));  
   printf("%zu ", offsetof(S, j));  
   printf("%zu\n", offsetof(S, k));  
  
   printf("%zu ", offsetof(T, i));  
   printf("%zu ", offsetof(T, j));  
   printf("%zu\n", offsetof(T, k));  
}  
```  
  
```  
0 4 8  
0 4 6  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób użycia **wypychania**, **pop**, i **Pokaż** składni.  
  
```  
// pragma_directives_pack_2.cpp  
// compile with: /W1 /c  
#pragma pack()   // n defaults to 8; equivalent to /Zp8  
#pragma pack(show)   // C4810  
#pragma pack(4)   // n = 4  
#pragma pack(show)   // C4810  
#pragma pack(push, r1, 16)   // n = 16, pushed to stack  
#pragma pack(show)   // C4810  
#pragma pack(pop, r1, 2)   // n = 2 , stack popped  
#pragma pack(show)   // C4810  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)