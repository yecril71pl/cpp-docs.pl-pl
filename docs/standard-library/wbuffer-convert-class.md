---
title: "wbuffer_convert — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
dev_langs:
- C++
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0153bf7d40dbd4290900d15b6e68d84d0c07869
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="wbufferconvert-class"></a>wbuffer_convert — Klasa
W tym artykule opisano buforu strumienia, który kontroluje przesyłania elementów do i z buforu strumienia bajtów.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
 : public std::basic_streambuf<Elem, Traits>
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Codecvt`|[Ustawień regionalnych](../standard-library/locale-class.md) aspektu reprezentujący obiekt konwersji.|  
|`Elem`|Typ elementu znaków dwubajtowych.|  
|`Traits`|Cechy skojarzone z *elementu*.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa szablonu opisuje buforu strumienia, który kontroluje przekazywania elementów typu `_Elem`, którego cech znaków są opisane w klasie `Traits`, do i z buforu strumienia bajtów typu `std::streambuf`.  
  
 Konwersja między sekwencji `Elem` wartości i wielobajtowych sekwencji jest wykonywane przez obiekt klasy `Codecvt<Elem, char, std::mbstate_t>`, które spełnia wymagania aspekt konwersja standardowa kodu `std::codecvt<Elem, char, std::mbstate_t>`.  
  
 Przechowuje obiekt tej klasy szablonu:  
  
-   Wskaźnik do podstawowego buforu strumienia bajtów  
  
-   Wskaźnik do obiektu przydzielone konwersji (czyli zwolniony, kiedy [wbuffer_convert —](../standard-library/wbuffer-convert-class.md)
