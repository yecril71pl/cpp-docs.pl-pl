---
title: Korzystanie z operatorów wyodrębniania
ms.date: 11/04/2016
helpviewer_keywords:
- extraction operators [C++]
- '&gt;&gt; operator [C++], extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
ms.openlocfilehash: 1fc6ffd2f033dfe3df60260f734d93b79d6824f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362429"
---
# <a name="using-extraction-operators"></a>Korzystanie z operatorów wyodrębniania

Operator wyodrębniania (`>>`), który jest wcześniej zaplanowane dla wszystkich standardowych typów danych języka C++ jest najprostszym sposobem na uzyskiwanie bajtów na obiekt strumienia wejściowego.

Operatory wyodrębniania wprowadzania tekstu sformatowanego zależą od biały znak do oddzielania wartości danych przychodzących. Jest to wygodne, gdy pole tekstowe zawiera wiele wyrazów lub przecinków oddzielić liczby. W takim przypadku jeden alternatywą jest użycie funkcji niesformatowany element członkowski danych wejściowych [istream::getline](../standard-library/basic-istream-class.md#getline) odczytać blok tekstu z białą przestrzenią uwzględnione, a następnie analizować bloku przy użyciu specjalnych funkcji. Inną metodą jest pochodną klasy strumienia wejściowego z funkcją składową takich jak `GetNextToken`, który można wywoływać członków istream wyodrębnić i sformatować dane znakowe.

## <a name="see-also"></a>Zobacz także

[Strumienie wejściowe](../standard-library/input-streams.md)<br/>
