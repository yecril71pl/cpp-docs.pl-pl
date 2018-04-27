---
title: Korzystanie z operatorów wyodrębniania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- extraction operators [C++]
- '&gt;&gt; operator [C++], extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 26dec4b3bdad481e53e88ca2c91c82161de9bf81
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="using-extraction-operators"></a>Korzystanie z operatorów wyodrębniania

Operator wyodrębniania (`>>`), który jest wcześniej zaplanowane dla wszystkie standardowe typy danych języka C++ jest najprostszym sposobem pobrania bajtów ze strumienia wejściowego obiektu.

Operatory wyodrębniania wejściowy tekst sformatowany zależą od biały znak przychodzące wartości danych. Jest to niewygodne, gdy pole tekstowe zawiera wiele słów lub gdy numery oddziel przecinkami. W takim przypadku jeden alternatywą jest użycie funkcji niesformatowany wejściowy element członkowski [istream::getline](../standard-library/basic-istream-class.md#getline) do odczytu bloku tekstu z białą przestrzenią włączone, a następnie analizować bloku specjalne funkcje. Inną metodą jest pochodzi z klasy strumienia wejściowego z funkcją członkowską takich jak `GetNextToken`, który można wywołać członków istream wyodrębnić i formatowania danych znakowych.

## <a name="see-also"></a>Zobacz także

[Strumienie wejściowe](../standard-library/input-streams.md)<br/>
