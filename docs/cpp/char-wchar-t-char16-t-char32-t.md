---
title: char, wchar_t, char16_t, char32_t | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- char_cpp
- char16_t_cpp
- wchar_t_cpp
- char32_t_cpp
dev_langs: C++
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c01d4718bbc1781ea4705945bb90874384e09058
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="char-wchart-char16t-char32t"></a>char, wchar_t, char16_t, char32_t
Typy, które reprezentują znaki alfanumeryczne oraz symbole inne niż alfanumeryczne oraz znaki niedrukowalne wbudowane typy char, wchar_t, char16_t i char32_t. znak jest 8 rozmiar, wchar_t i char16_t są 16 bitów o rozmiarze i char32_t jest 32-bitowy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
char     ch1{ 'a' };    
wchar_t  ch2{ 'a' }; // or {L'a'}    
char16_t ch3{ L'a' };// or {L'a'}    
char32_t ch4{ L'a' };// or {L'a'}  
```  
  
## <a name="remarks"></a>Uwagi  
 `char` Typu została oryginalnego typu znaków w C i C++. Może służyć do przechowywania znaki z zestawu znaków ASCII lub dowolne zestawów znaków ISO 8859 lub zestaw znaków UTF-8. Typ `unsigned char` jest często używana do reprezentowania *bajtów* który nie jest typem wbudowanym w języku C++. Typ char nie jest odpowiedni dla tekstu w wielu językach. Ogólnie rzecz biorąc nowoczesny programy należy używać jednego z typów znaków typu wide do reprezentowania tekstu. Jest Unicode  
  
 W standardowej bibliotece C++ typu basic_string — jest przeznaczone dla ciągów zarówno wąskie i dwubajtowe. Za pomocą std::string znaki są Typ char i std::wstring przypadku o typ wchar_t znaki. Inne typy, które reprezentują tekst, w tym std::stringstream i std::cout ma specjalizacje wąskie i dwubajtowe ciągów.  
  
