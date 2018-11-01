---
title: Ostrzeżenie kompilatora (poziom 1) C4462
ms.date: 10/25/2017
f1_keywords:
- C4462
helpviewer_keywords:
- C4462
ms.assetid: 4e20aca4-293e-4c75-a83d-961c27ab7840
ms.openlocfilehash: 801a440f131e9428c7f217346a6fd26c72cc1374
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582328"
---
# <a name="compiler-warning-level-1-c4462"></a>Ostrzeżenie kompilatora (poziom 1) C4462

> nie można określić GUID typu. Program może ulec awarii w czasie wykonywania.

Ostrzeżenie C4462 występuje w środowiska uruchomieniowego Windows aplikacji lub składnika, gdy publiczny `TypedEventHandler` ma jako jeden z jego parametrów typu odwołanie do klasy otaczającej.

To ostrzeżenie zostanie automatycznie podwyższony do błędu. Jeśli chcesz zmienić to zachowanie, użyj [ostrzeżenie #pragma](../../preprocessor/warning.md). Na przykład aby C4462 do poziomu 4 ostrzeżenie problem, Dodaj ten wiersz do pliku kodu źródłowego:

```cpp
#pragma warning(4:4462)
```

## <a name="example"></a>Przykład

Ten przykład generuje ostrzeżenie C4462:

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

Identyfikator GUID typu `Windows::Foundation::TypedEventHandler<R^, EventArgs^>^` jest używany tylko, gdy typ jest dostępny z innego składnika. Pierwsza metoda obejścia problemu jest skuteczna, ponieważ może on być dostępny wyłącznie w ramach własnego składnika po zastosowaniu obejścia. W przeciwnym razie kompilator musi założyć najgorszy przypadek i wygenerować ostrzeżenie.
