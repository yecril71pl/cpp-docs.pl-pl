---
title: Korzystanie z operatorów wyodrębniania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- extraction operators [C++]
- '&gt;&gt; operator [C++], extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96dc02c8bcd82c5b26d3cef71aa2085913ea259d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="using-extraction-operators"></a>Korzystanie z operatorów wyodrębniania

Operator wyodrębniania (`>>`), który jest wcześniej zaplanowane dla wszystkie standardowe typy danych języka C++ jest najprostszym sposobem pobrania bajtów ze strumienia wejściowego obiektu.

Operatory wyodrębniania wejściowy tekst sformatowany zależą od biały znak przychodzące wartości danych. Jest to niewygodne, gdy pole tekstowe zawiera wiele słów lub gdy numery oddziel przecinkami. W takim przypadku jeden alternatywą jest użycie funkcji niesformatowany wejściowy element członkowski [istream::getline](../standard-library/basic-istream-class.md#getline) do odczytu bloku tekstu z białą przestrzenią włączone, a następnie analizować bloku specjalne funkcje. Inną metodą jest pochodzi z klasy strumienia wejściowego z funkcją członkowską takich jak `GetNextToken`, który można wywołać członków istream wyodrębnić i formatowania danych znakowych.

## <a name="see-also"></a>Zobacz także

[Strumienie wejściowe](../standard-library/input-streams.md)<br/>
