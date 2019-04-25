---
title: Tworzenie wystąpienia szablonu funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- function templates, instantiation
- instantiation, function templates
ms.assetid: f22a07c7-3ad1-465a-84f5-8737e274bd47
ms.openlocfilehash: c4667f5ae625468cdab428706ddaff92a1c1af33
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154181"
---
# <a name="function-template-instantiation"></a>Tworzenie wystąpienia szablonu funkcji

Gdy szablon funkcji najpierw jest wywoływana dla każdego typu, kompilator utworzy podczas tworzenia wystąpienia. Każdego wystąpienia to wersja z szablonem funkcji przeznaczone specjalnie do tego typu. Za każdym razem, gdy jest używana funkcja dla danego typu zostanie wywołana tego wystąpienia. Jeśli masz kilka wystąpień identyczny, nawet w przypadku różnych modułów, tylko jedna kopia utworzenia wystąpienia zakończą się w pliku wykonywalnym.

Konwersja argumenty funkcji jest dozwolona w szablonów funkcji dla każdej pary argumentów i parametrów, gdy parametr nie zależy od argumentu szablonu.

Szablony funkcji można jawnie tworzone przez zadeklarowanie szablonu przy użyciu określonego typu jako argumentu. Na przykład poniższy kod jest dozwolony:

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

## <a name="see-also"></a>Zobacz także

[Szablony funkcji](../cpp/function-templates.md)