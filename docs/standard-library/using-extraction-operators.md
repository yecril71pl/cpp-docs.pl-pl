---
title: Korzystanie z operatorów wyodrębniania
ms.date: 11/04/2016
helpviewer_keywords:
- extraction operators [C++]
- '&gt;&gt; operator [C++], extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
ms.openlocfilehash: 7950984973f8df236905128ce4b5336ecb874b7f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458035"
---
# <a name="using-extraction-operators"></a>Korzystanie z operatorów wyodrębniania

Operator wyodrębniania (`>>`), który jest zaprogramowany dla wszystkich standardowych C++ typów danych, jest najprostszym sposobem uzyskania bajtów z obiektu strumienia wejściowego.

Operatory wyodrębniania tekstu sformatowanego są zależne od odstępu, aby oddzielić wartości danych przychodzących. Jest to niewygodne, gdy pole tekstowe zawiera wiele słów lub przecinki oddzielające cyfry. W takim przypadku jedną alternatywą jest użycie niesformatowanej wejściowej funkcji członkowskiej [IStream:: getline](../standard-library/basic-istream-class.md#getline) , aby odczytać blok tekstu z dołączonym białym znakiem, a następnie przeanalizować blok przy użyciu funkcji specjalnych. Inna metoda polega na utworzeniu klasy strumienia wejściowego z funkcją składową, taką `GetNextToken`jak, która może wywoływać IStream członków, aby wyodrębnić i sformatować dane znakowe.

## <a name="see-also"></a>Zobacz także

[Strumienie wejściowe](../standard-library/input-streams.md)
