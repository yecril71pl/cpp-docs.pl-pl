---
title: Wskaźniki [C++]
ms.date: 11/19/2019
description: Informacje o nieprzetworzonych wskaźnikach i inteligentnych wskaźnikach w języku Microsoft C++.
helpviewer_keywords:
- pointers (C++)
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
ms.openlocfilehash: 485cee667fa288bff76fdeac7c9f229355c276d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371914"
---
# <a name="pointers-c"></a>Wskaźniki [C++]

Wskaźnik jest zmienną, która przechowuje adres pamięci obiektu. Wskaźniki są szeroko stosowane zarówno w językach C, jak i C++ do trzech głównych celów:

- aby przydzielić nowe obiekty na stercie,
- przekazywania funkcji do innych funkcji
- iteracji nad elementami w tablicach lub innych strukturach danych.

W programowaniu w stylu C *nieprzetworzone wskaźniki* są używane dla wszystkich tych scenariuszy. Jednak surowe wskaźniki są źródłem wielu poważnych błędów programowania. W związku z tym ich użycie jest zdecydowanie odradzane, z wyjątkiem przypadków, gdy zapewniają one znaczące korzyści wydajności i nie ma dwuznaczności co do tego, który wskaźnik jest *wskaźnikiem posiadania,* który jest odpowiedzialny za usunięcie obiektu. Nowoczesne C++ zapewnia *inteligentne wskaźniki* do przydzielania obiektów, *iteratory* do przechodzenia przez struktury danych i *wyrażenia lambda* do przekazywania funkcji. Za pomocą tych obiektów języka i biblioteki zamiast nieprzetworzonych wskaźników, można uczynić program bezpieczniejsze, łatwiejsze do debugowania i łatwiejsze do zrozumienia i utrzymania. Aby uzyskać więcej informacji, zobacz [Inteligentne wskaźniki,](smart-pointers-modern-cpp.md) [Iteratory](../standard-library/iterators.md)i [Wyrażenia Lambda.](lambda-expressions-in-cpp.md)

## <a name="in-this-section"></a>W tej sekcji

- [Wskaźniki podstawowe](raw-pointers.md)
- [Wskaźniki konsetryj i lotne](const-and-volatile-pointers.md)
- [nowe i usuwaj operatory](new-and-delete-operators.md)
- [Wskaźniki inteligentne](smart-pointers-modern-cpp.md)
- [Jak: Tworzenie i używanie unique_ptr wystąpień](how-to-create-and-use-unique-ptr-instances.md)
- [Jak: Tworzenie i używanie shared_ptr wystąpień](how-to-create-and-use-shared-ptr-instances.md)
- [Jak: Tworzenie i używanie weak_ptr wystąpień](how-to-create-and-use-weak-ptr-instances.md)
- [Jak: Tworzenie i używanie wystąpień CComPtr i CComQIPtr](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)

## <a name="see-also"></a>Zobacz też

[Iteratory](../standard-library/iterators.md)</br>
[Wyrażenia lambda](lambda-expressions-in-cpp.md)
