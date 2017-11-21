---
title: "Korzystanie z operatorów wyodrębniania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- extraction operators [C++]
- '&gt;&gt; operator [C++], extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ae55b0dfed94383ab4d70700a4f2b39ff8e8ea62
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-extraction-operators"></a>Korzystanie z operatorów wyodrębniania
Operator wyodrębniania (`>>`), który jest wcześniej zaplanowane dla wszystkie standardowe typy danych języka C++ jest najprostszym sposobem pobrania bajtów ze strumienia wejściowego obiektu.  
  
 Operatory wyodrębniania wejściowy tekst sformatowany zależą od biały znak przychodzące wartości danych. Jest to niewygodne, gdy pole tekstowe zawiera wiele słów lub gdy numery oddziel przecinkami. W takim przypadku jeden alternatywą jest użycie funkcji niesformatowany wejściowy element członkowski [istream::getline](../standard-library/basic-istream-class.md#getline) do odczytu bloku tekstu z białą przestrzenią włączone, a następnie analizować bloku specjalne funkcje. Inną metodą jest pochodzi z klasy strumienia wejściowego z funkcją członkowską takich jak `GetNextToken`, który można wywołać członków istream wyodrębnić i formatowania danych znakowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Strumienie wejściowe](../standard-library/input-streams.md)

