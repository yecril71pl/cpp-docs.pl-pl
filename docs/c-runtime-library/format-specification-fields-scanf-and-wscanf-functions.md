---
title: 'Pola specyfikacji formatu: funkcji wscanf | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- wscanf
- scanf
dev_langs: C++
helpviewer_keywords:
- width, specifications in scanf function
- scanf format specifications
- scanf width specifications
- scanf type field characters
- type fields, scanf function
- format specification fields for scanf function
- type fields
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2286d7a6b82cf917c264cc43b82dec3939af6d94
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="format-specification-fields-scanf-and-wscanf-functions"></a>Pola specyfikacji formatu dla funkcji wscanf
Informacje w tym miejscu ma zastosowanie do całej `scanf` rodziny funkcji, łącznie z wersjami bezpiecznego i opisano symbole używane mówić `scanf` działa jak przeanalizować strumienia wejściowego, takich jak strumień wejściowy `stdin` dla `scanf`, na wartości, które są wstawiane do zmiennych programu.  
  
 Specyfikacji formatu ma następujący format:  
  
 `%`[`*`] [[szerokość](../c-runtime-library/scanf-width-specification.md)] [{[h &#124; l &#124; wszystki &#124; Komputerach 64 &#124; L](../c-runtime-library/scanf-width-specification.md)}][typu](../c-runtime-library/scanf-type-field-characters.md)  
  
 `format` Argument określa interpretacji danych wejściowych i może zawierać jeden lub więcej z następujących czynności:  
  
-   Znak odstępu: pusty (""); Karta ("\t"); lub nowego wiersza ("\n"). Biały znak powoduje, że `scanf` do odczytu, ale nie przechowywane, wszystkich kolejnych znaków odstępu w danych wejściowych do następny znak z systemem innym niż biały. Biały znak w formacie dopasowuje dowolną liczbę (w tym 0) i kombinację znaków odstępu w danych wejściowych.  
  
-   Znaki inne niż biały znak, z wyjątkiem znaku procentu (`%`). Powoduje, że system inny niż biały znak `scanf` do odczytu, ale nie przechowywane, zgodnych z systemem innym niż — biały znak. Niezgodna następny znak w strumieniu wejściowym `scanf` kończy.  
  
-   Format specyfikacje wprowadzone przez znaku procentu (`%`). Powoduje, że specyfikacji formatu `scanf` do odczytywania i konwertować znaków w danych wejściowych do wartości określonego typu. Wartość jest przypisany do argumentu na liście argumentów.  
  
 Format jest odczytywany od lewej do prawej. Znaki poza specyfikacje formatu powinny odpowiadać sekwencja znaków w strumieniu wejściowym; pasujących znaków w strumieniu wejściowym są skanowane, ale nie są przechowywane. Jeśli znak w strumieniu wejściowym niezgodne ze specyfikacją formatu `scanf` kończy, i pozostanie znak w strumieniu wejściowym tak, jakby była nie został odczytany.  
  
 W przypadku pierwszego specyfikacji formatu wartość pierwszego pola wejściowego jest konwertowane zgodnie ze specyfikacją i przechowywane w lokalizacji określonej przez pierwszy `argument`. Drugi specyfikacji formatu powoduje, że drugie pole wejściowe przekonwertować i przechowywać w ciągu sekundy `argument`, i tak dalej do końca ciągu formatu.  
  
 Nie zdefiniowano pola wejściowego jako wszystkie znaki do pierwszego znaku spacji (miejsce, karty lub nowego wiersza) lub do pierwszego znaku, której nie można przekonwertować zgodnie ze specyfikacją formatu lub do szerokości pola (Jeśli określono) zostanie osiągnięty. Jeśli istnieje za dużo argumentów dla danego specyfikacje, dodatkowe argumenty zostały obliczone, ale ignorowane. Wyniki są nieprzewidywalne, jeśli nie ma za mało argumentów dla specyfikacji formatu.  
  
 Każdego pola specyfikacji formatu jest pojedynczy znak lub oznaczający opcja określony format liczby. `type` Znak, który pojawia się po ostatnim pole opcjonalne format, określa, czy pole wejściowe jest interpretowana jako znak, ciągu lub liczbą.  
  
 Najprostsza specyfikacji formatu zawiera znak procentu i `type` znaku (na przykład `%s`). Jeśli znaku procentu (`%`) następuje znak czy ma znaczenia jako znaku kontrolnego formatu, który znak i następujące znaki (do następnej znak procentu) są traktowane jako zwykłej sekwencji znaków, to znaczy sekwencji znaki, które muszą być zgodne z danych wejściowych. Na przykład aby określić procent znak ma być danych wejściowych, należy użyć `%%`.  
  
 Znak gwiazdki (`*`) po znaku procentu pomija przypisania dalej pola wejściowego, który jest interpretowany jako pole określonego typu. Pole jest skanowany, ale nie są przechowywane.  
  
 Bezpieczne wersji (z `_s` sufiks) z `scanf` rodziny funkcji wymagają, aby parametr rozmiaru buforu można przekazać bezpośrednio po każdego parametru typu `c`, `C`, `s`, `S`lub `[`. Aby uzyskać więcej informacji o wersjach bezpiecznego `scanf` rodziny funkcji, zobacz [scanf_s —, _scanf_s_l —, wscanf_s —, _wscanf_s_l —](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md).  
  
## <a name="see-also"></a>Zobacz też  
 [scanf — specyfikacje szerokości](../c-runtime-library/scanf-width-specification.md)   
 [scanf — znaki pola typu](../c-runtime-library/scanf-type-field-characters.md)   
 [scanf, _scanf_l —, wscanf — _wscanf_l —](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)