---
title: Dodawania (+) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- pointers, adding integers
ms.assetid: b9014fee-825d-46ef-91db-5d46807081fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 62ed952113f3d8b3db46ac735ade4d2e9850dc97
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090857"
---
# <a name="addition-"></a>Dodawanie (+)

Operator dodawania (**+**) powoduje, że dwóch argumentów operacji do dodania. Oba operandy może być typu całkowitego lub zmiennoprzecinkowego typy, lub jeden argument może być wskaźnika, a drugi liczbą całkowitą.

Po dodaniu do wskaźnika, wartość całkowitą liczbą całkowitą (*i*) jest konwertowana mnożąc przez rozmiar wartości, odnoszący się do wskaźnika. Po konwersji na wartość całkowitą reprezentuje *i* pozycji pamięci, w którym każdej pozycji ma długość określona przez typ wskaźnika. Gdy wartość przekonwertowana liczba całkowita jest dodawana do wartości wskaźnika, wynik jest wartością wskaźnika reprezentująca adres *i* pozycji z oryginalnego adresu. Nowa wartość wskaźnika adresów wartości tego samego typu jak oryginalna wartość wskaźnika, a w związku z tym jest taka sama jak indeksowanie tablicy (zobacz [tablic One-Dimensional](../c-language/one-dimensional-arrays.md) i [tablic wielowymiarowych](../c-language/multidimensional-arrays-c.md)). Jeżeli wskaźnik Suma punktów spoza tablicy, z wyjątkiem w pierwszej lokalizacji poza najwyższych, wynik jest niezdefiniowany. Aby uzyskać więcej informacji, zobacz [arytmetyki wskaźnika](../c-language/pointer-arithmetic.md).

## <a name="see-also"></a>Zobacz też

[Operatory dodawania języka C](../c-language/c-additive-operators.md)