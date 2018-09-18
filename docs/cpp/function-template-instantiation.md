---
title: Tworzenie wystąpienia szablonu funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- templates, instantiation
- function templates, instantiation
- instantiation, function templates
ms.assetid: f22a07c7-3ad1-465a-84f5-8737e274bd47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb94a54c4f99b79e3be742c5b1448151cff140c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116792"
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