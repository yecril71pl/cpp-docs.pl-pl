---
title: Jawne tworzenie wystąpienia
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
ms.openlocfilehash: 0b1290bc23c56c0f35ddd3bb93e37ce4f5f0d2ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361963"
---
# <a name="explicit-instantiation"></a>Jawne tworzenie wystąpienia

Można użyć jawnego wystąpienia, aby utworzyć wystąpienie klasy lub funkcji szablonu bez faktycznego użycia go w kodzie. Ponieważ jest to przydatne podczas tworzenia plików biblioteki (lib), które używają szablonów do dystrybucji, definicje szablonów nie są umieszczane w plikach obiektów (obj).

Ten kod jawnie `MyStack` wystąpienia dla zmiennych **int** i sześć elementów:

```cpp
template class MyStack<int, 6>;
```

Ta instrukcja tworzy wystąpienia `MyStack` bez rezerwacji magazynu dla obiektu. Kod jest generowany dla wszystkich elementów członkowskich.

Następny wiersz jawnie tworzy tylko funkcję elementu członkowskiego konstruktora:

```cpp
template MyStack<int, 6>::MyStack( void );
```

Można jawnie utworzyć wystąpienia szablonów funkcji przy użyciu określonego argumentu typu, aby ponownie je zadeklarować, jak pokazano w przykładzie w [wystąpieniu szablonu funkcji](../cpp/function-template-instantiation.md).

Można użyć **extern** słowa kluczowego, aby zapobiec automatycznemu wystąpieniu członków. Przykład:

```cpp
extern template class MyStack<int, 6>;
```

Podobnie można oznaczyć określonych członków jako zewnętrznych i nie wystąpienia:

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

Za pomocą słowa kluczowego **extern** można zachować kompilatora z generowania tego samego kodu wystąpienia w więcej niż jeden moduł obiektu. Należy utworzyć wystąpienie funkcji szablonu przy użyciu określonych parametrów szablonu jawne w co najmniej jeden moduł połączony, jeśli funkcja jest wywoływana lub otrzymasz błąd konsolidatora podczas tworzenia programu.

> [!NOTE]
> **Extern** — słowo kluczowe w specjalizacji dotyczy tylko funkcji członkowskich zdefiniowanych poza treścią klasy. Funkcje zdefiniowane wewnątrz deklaracji klasy są uważane za funkcje wbudowane i są zawsze tworzone.

## <a name="see-also"></a>Zobacz też

[Szablony funkcji](../cpp/function-templates.md)
