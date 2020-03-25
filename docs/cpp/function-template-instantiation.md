---
title: Tworzenie wystąpienia szablonu funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- function templates, instantiation
- instantiation, function templates
ms.assetid: f22a07c7-3ad1-465a-84f5-8737e274bd47
ms.openlocfilehash: 6917448af067542fffb13aa043720bf8a26f7ba3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179760"
---
# <a name="function-template-instantiation"></a>Tworzenie wystąpienia szablonu funkcji

Po pierwszym wywołaniu szablonu funkcji dla każdego typu kompilator tworzy Tworzenie wystąpienia. Każde wystąpienie jest wersją funkcji szablonu wyspecjalizowaną dla typu. To wystąpienie będzie wywoływane za każdym razem, gdy funkcja zostanie użyta dla tego typu. Jeśli masz kilka identycznych wystąpień, nawet w różnych modułach, tylko jedna kopia wystąpienia zostanie zakończona w pliku wykonywalnym.

Konwersja argumentów funkcji jest dozwolona w szablonach funkcji dla dowolnego argumentu i pary parametrów, gdzie parametr nie zależy od argumentu szablonu.

Szablony funkcji można jawnie utworzyć, deklarując szablon z określonym typem jako argumentem. Na przykład następujący kod jest dozwolony:

```cpp
// function_template_instantiation.cpp
template<class T> void f(T) { }

// Instantiate f with the explicitly specified template.
// argument 'int'
//
template void f<int> (int);

// Instantiate f with the deduced template argument 'char'.
template void f(char);
int main()
{
}
```

## <a name="see-also"></a>Zobacz też

[Szablony funkcji](../cpp/function-templates.md)
