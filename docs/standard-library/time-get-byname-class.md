---
title: "time_get_byname — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xloctime/std::time_get_byname
dev_langs:
- C++
helpviewer_keywords:
- time_get_byname class
ms.assetid: 6e54153e-da40-4bb9-a942-1a6ce57b30c9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5da50c2079fe7345d2ac70855f0fb57c8eeecce7
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="timegetbyname-class"></a>time_get_byname — Klasa
Klasy pochodne szablonu opisuje obiekt, który może służyć jako zestaw reguł ustawień regionalnych typu `time_get` \<CharType, InputIterator >.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Elem, class InputIterator =
    istreambuf_iterator<CharType, char_traits<CharType>>>
class time_get_byname : public time_get<CharType, InputIterator>
{
public:
    explicit time_get_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_get_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_get_byname()
};
```  
  
#### <a name="parameters"></a>Parametry  
 `_Locname`  
 Nazwane ustawień regionalnych.  
  
 `_Refs`  
 Liczba początkowa odwołania.  
  
## <a name="requirements"></a>Wymagania  
 Jego zachowanie jest określany przez nazwany ustawień regionalnych `_Locname`. Każdy Konstruktor inicjuje jego obiektu podstawowego z [time_get —](../standard-library/time-get-class.md#time_get)\<CharType, InputIterator > ( `_Refs`).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ustawień regionalnych >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



