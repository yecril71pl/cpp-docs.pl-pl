---
title: Kompilator ostrzegawcze (poziom 1) C4462 | Dokumentacja firmy Microsoft
ms.date: 10/25/2017
ms.technology: cpp-tools
ms.topic: error-reference
f1_keywords: C4462
dev_langs: C++
helpviewer_keywords: C4462
ms.assetid: 4e20aca4-293e-4c75-a83d-961c27ab7840
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 95fef51c6b96146842413cd52ab203b747247398
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4462"></a>Ostrzeżenie kompilatora (poziom 1) C4462

> nie można określić GUID typu. Program może ulec awarii w czasie wykonywania.

Ostrzeżenie C4462 odbywa się w aplikacji środowiska wykonawczego systemu Windows lub składnik, gdy publiczny `TypedEventHandler` zawiera jako jeden z jego parametrów typu odwołanie do klasy otaczającej.

To ostrzeżenie zostanie automatycznie podwyższony do wystąpił błąd. Jeśli chcesz zmienić to zachowanie, użyj [ostrzeżenie #pragma](../../preprocessor/warning.md). Na przykład aby C4462 na poziom 4 ostrzeżenie problem, Dodaj ten wiersz do pliku kodu źródłowego:

```cpp
#pragma warning(4:4462)
```

## <a name="example"></a>Przykład

W tym przykładzie generuje ostrzeżenie C4462:

```cpp
namespace N
{
       public ref struct EventArgs sealed {};
       public ref struct R sealed
       {
              R() {}
              event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
       };
}

[Platform::MTAThread]
int main()
{
     auto x = ref new N::R();
}
```

Istnieją dwa sposoby obejścia tego błędu. Jednym ze sposobów, pokazanym w następnym przykładzie, jest zapewnienie zdarzeniu wewnętrznej dostępności, tak aby było ono dostępne dla kodu w tym samym pliku wykonywalnym, ale nie dla kodu w innych składnikach systemu Windows czasu wykonywania.

```cpp
internal:
    event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
```

Jeśli zdarzenie musi być publiczne, można użyć innego obejścia, które polega na uwidocznieniu go przez interfejs domyślny:

```cpp
ref struct R;
public interface struct IR{ event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;};

public ref struct R sealed : [Windows::Foundation::Metadata::Default] IR
{
    R() {}
    virtual event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
};
```

Identyfikator GUID typu `Windows::Foundation::TypedEventHandler<R^, EventArgs^>^` jest używana tylko w przypadku dostępu do typu z innego składnika. Pierwsza metoda obejścia problemu jest skuteczna, ponieważ może on być dostępny wyłącznie w ramach własnego składnika po zastosowaniu obejścia. W przeciwnym razie kompilator musi założyć najgorszy przypadek i wygenerować ostrzeżenie.
