---
title: Ostrzeżenie kompilatora (poziom 4) C4121
ms.date: 11/04/2016
f1_keywords:
- C4121
helpviewer_keywords:
- C4121
ms.assetid: 8c5b85c9-2543-426b-88bc-319c50158c7e
ms.openlocfilehash: 0e5bdab6ff0d0508abaf5f726d1356102cfca04a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219979"
---
# <a name="compiler-warning-level-4-c4121"></a>Ostrzeżenie kompilatora (poziom 4) C4121

'symbol' : wyrównanie elementu członkowskiego było wrażliwe na pakowanie

Kompilator dodał dopełnienie, aby wyrównać element członkowski struktury na granicy pakowania, ale wartość pakowania jest mniejsza niż rozmiar tego elementu. Na przykład poniższy fragment kodu powoduje C4121:

```cpp
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

- Zmień rozmiar pakowania na rozmiar elementu członkowskiego, który spowodował ostrzeżenie, lub większy rozmiar. Na przykład w tym fragmencie kodu Zmień `pack(2)` na `pack(4)` lub `pack(8)` .

- Zmień kolejność deklaracji elementów członkowskich według rozmiarów, od największych do najmniejszych. W tym fragmencie kodu Odwróć kolejność elementów członkowskich struktury, tak aby **`long long`** członek poprzedzał **`int`** , i **`int`** poprzedza **`char`** .

To ostrzeżenie występuje tylko, gdy kompilator dodaje dopełnienie przed elementami członkowskimi. Nie następuje, gdy pakowanie umieściło dane w lokalizacji w pamięci, która nie jest dostosowana dla tego typu danych, ale nie umieszczono dopełnienia przed elementem członkowskim. Gdy dane nie są wyrównane na granicach, które stanowią wielokrotność rozmiaru danych, sprawność działania może się zmniejszyć. Odczytywanie i zapisywanie niewyrównanych danych powoduje usterki procesora w niektórych architekturach, a znalezienie i usunięcie problemów może zająć czas dwa, a nawet trzy rzędy wielkości dłuższy niż normalnie. Dostępów do niewyrównanych danych nie można przenieść na niektóre architektury RISC.

Aby określić wyrównanie struktury, można użyć [#pragma Pack](../../preprocessor/pack.md) lub [/ZP](../../build/reference/zp-struct-member-alignment.md) . (Kompilator nie generuje tego ostrzeżenia, jeśli określono **/ZP1** ).
