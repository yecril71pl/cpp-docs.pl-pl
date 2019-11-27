---
title: Wskaźniki (C++)
ms.date: 11/19/2019
description: Informacje o surowych wskaźnikach i inteligentnych C++wskaźnikach w firmie Microsoft.
helpviewer_keywords:
- pointers (C++)
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
ms.openlocfilehash: 21dcc55048e9e378f370f25254e1910b05e49d69
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246423"
---
# <a name="pointers-c"></a>Wskaźniki (C++)

Wskaźnik to zmienna, która przechowuje adres pamięci obiektu. Wskaźniki są szeroko używane zarówno w języku C, C++ jak i na trzy główne cele:

- Aby przydzielić nowe obiekty na stercie,
- Aby przekazać funkcje do innych funkcji
- do iteracji nad elementami w tablicach lub w innych strukturach danych.

W programowaniu w stylu języka C, *surowe wskaźniki* są używane we wszystkich tych scenariuszach. Jednak surowe wskaźniki są źródłem wielu poważnych błędów programistycznych. W związku z tym ich użycie jest zdecydowanie odradzane, z tą różnicą, że zapewniają znaczącą korzyść wydajności i nie ma niejednoznaczności, ponieważ wskaźnik jest *wskaźnikiem będącym właścicielem* , który jest odpowiedzialny za usunięcie obiektu. Nowoczesne C++ oferuje *inteligentne wskaźniki* do alokowania obiektów, *iteratorów* dla przechodzenia struktur danych i *wyrażeń lambda* do przekazywania funkcji. Korzystając z tych funkcji językowych i bibliotek zamiast nieprzetworzonych wskaźników, zapewniasz, że program będzie bezpieczniejszy, łatwiejszy w debugowaniu i łatwiejszy do zrozumienia i utrzymania. Aby uzyskać więcej informacji, zobacz [inteligentne wskaźniki](smart-pointers-modern-cpp.md), [Iteratory](../standard-library/iterators.md)i [wyrażenia lambda](lambda-expressions-in-cpp.md) .

## <a name="in-this-section"></a>W tej sekcji

- [Surowe wskaźniki](raw-pointers.md)
- [Wskaźniki const i volatile](const-and-volatile-pointers.md)
- [New i DELETE — operatory](new-and-delete-operators.md)
- [Inteligentne wskaźniki](smart-pointers-modern-cpp.md)
- [Instrukcje: Tworzenie wystąpień unique_ptr i korzystanie z nich](how-to-create-and-use-unique-ptr-instances.md)
- [Instrukcje: Tworzenie wystąpień shared_ptr i korzystanie z nich](how-to-create-and-use-shared-ptr-instances.md)
- [Instrukcje: Tworzenie wystąpień weak_ptr i korzystanie z nich](how-to-create-and-use-weak-ptr-instances.md)
- [Instrukcje: Tworzenie wystąpień CComPtr i CComQIPtr oraz korzystanie z nich](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)

## <a name="see-also"></a>Zobacz także

[Iteratory](../standard-library/iterators.md)</br>
[Wyrażenia lambda](lambda-expressions-in-cpp.md)
