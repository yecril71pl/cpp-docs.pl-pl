---
title: Jawne tworzenie wystąpienia
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
ms.openlocfilehash: dbe8bebf91a174e07c7c5cce8e9caf1cf3432edf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180033"
---
# <a name="explicit-instantiation"></a>Jawne tworzenie wystąpienia

Można użyć jawnego tworzenia wystąpienia, aby utworzyć wystąpienie klasy lub funkcji z szablonem bez faktycznego używania jej w kodzie. Ponieważ jest to przydatne w przypadku tworzenia plików biblioteki (. lib), które używają szablonów do dystrybucji, definicje szablonu bez wystąpień nie są umieszczane w plikach obiektu (. obj).

Ten kod jawnie tworzy wystąpienie `MyStack` dla zmiennych **int** i sześciu elementów:

```cpp
template class MyStack<int, 6>;
```

Ta instrukcja tworzy Tworzenie wystąpienia `MyStack` bez rezerwowania żadnego magazynu dla obiektu. Kod jest generowany dla wszystkich elementów członkowskich.

Następny wiersz jawnie tworzy wystąpienie tylko funkcji członkowskiej konstruktora:

```cpp
template MyStack<int, 6>::MyStack( void );
```

Można jawnie utworzyć wystąpienia szablonów funkcji przy użyciu określonego argumentu typu, aby ponownie je zadeklarować, jak pokazano w przykładzie w [konkretyzacji szablonu funkcji](../cpp/function-template-instantiation.md).

Możesz użyć słowa kluczowego **extern** , aby zapobiec automatycznemu tworzeniu wystąpienia elementów członkowskich. Na przykład:

```cpp
extern template class MyStack<int, 6>;
```

Analogicznie, można oznaczyć określonych elementów członkowskich jako zewnętrzne i nie utworzyć wystąpienia:

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

Możesz użyć słowa kluczowego **extern** , aby uniemożliwić kompilatorowi generowanie tego samego kodu wystąpienia w więcej niż jednym module obiektu. Należy utworzyć wystąpienie funkcji szablonu przy użyciu określonych parametrów szablonu jawnego w co najmniej jednym połączonym module, jeśli funkcja jest wywoływana, lub podczas kompilowania programu wystąpi błąd konsolidatora.

> [!NOTE]
>  Słowo kluczowe **extern** w specjalizacji ma zastosowanie tylko do funkcji Członkowskich zdefiniowanych poza treścią klasy. Funkcje zdefiniowane wewnątrz deklaracji klasy są uznawane za wbudowane funkcje i zawsze są tworzone.

## <a name="see-also"></a>Zobacz też

[Szablony funkcji](../cpp/function-templates.md)
