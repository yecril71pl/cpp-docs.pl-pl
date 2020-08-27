---
title: Ostrzeżenie kompilatora (poziom 4) C4571
description: Dokumentuje C4571 z ostrzeżeniem kompilatora języka Microsoft C++.
ms.date: 08/24/2020
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 35f2b30a8ab7cfcc27ed7aae3aedd9bc81efacc8
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898548"
---
# <a name="compiler-warning-level-4-c4571"></a>Ostrzeżenie kompilatora (poziom 4) C4571

> Informacyjne: `catch(...)` semantyka zmieniła się od Visual C++ 7,1; wyjątki strukturalne (SEH) nie są już przechwytywane

C4571 jest generowany dla każdego `catch(...)` bloku po określeniu **`/EHs`** opcji kompilatora.

## <a name="remarks"></a>Uwagi

Po określeniu **`/EHs`** opcji kompilatora `catch(...)` bloki nie przechwytuje wyjątków strukturalnych. (Na przykład dzielenie przez zero lub wyjątki wskaźnika o wartości null). `catch(...)` Blok przechwytuje tylko jawnie zgłoszone wyjątki języka C++. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../../cpp/exception-handling-in-visual-cpp.md).

To ostrzeżenie jest domyślnie wyłączone.  Włącz to ostrzeżenie, aby upewnić się, że podczas kompilowania z **`/EHs`** `catch (...)` blokami nie będą przechwytywane wyjątki strukturalne. Aby uzyskać więcej informacji, zobacz [ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

Można rozwiązać C4571 w jeden z następujących sposobów:

- Kompiluj przy użyciu **`/EHa`** , jeśli nadal chcesz, `catch(...)` Aby bloki przechwycić wyjątki strukturalne.

- Nie włączaj C4571, jeśli nie chcesz `catch(...)` , aby bloki mogły przechwytywać wyjątki strukturalne, ale nadal chcesz używać `catch(...)` bloków.  Nadal można przechwytywać wyjątki strukturalne przy użyciu słów kluczowych obsługujących wyjątek strukturalny ( **`__try`** , **`__except`** i **`__finally`** ).  Pamiętaj jednak, że podczas kompilowania przy użyciu **`/EHs`** , destruktory są wywoływane tylko w przypadku zgłoszenia wyjątku C++, a nie w przypadku wystąpienia wyjątku SEH.

- Zastąp bloki blokami `catch(...)` catch dla określonych wyjątków c++ i opcjonalnie Dodaj obsługę wyjątków strukturalnych wokół obsługi wyjątków c++ ( **`__try`** , **`__except`** i **`__finally`** ).   Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków strukturalnych (C/C++)](../../cpp/structured-exception-handling-c-cpp.md) i [ `/EH` (model obsługi wyjątków)](../../build/reference/eh-exception-handling-model.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4571.

```cpp
// C4571.cpp
// compile with: /EHs /W4 /c
#pragma warning(default : 4571)
int main() {
   try {
      int i = 0, j = 1;
      j /= i;   // this will throw a SE (divide by zero)
   }
   catch(...) {}   // C4571 warning
}
```
