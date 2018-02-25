---
title: "time_put_byname — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xloctime/std::time_put_byname
dev_langs:
- C++
helpviewer_keywords:
- time_put_byname class
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 719df3a10b7c4b72cc90b0a5f8aad247cf915f4d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="timeputbyname-class"></a>time_put_byname — Klasa
Klasy pochodne szablonu opisuje obiekt, który może służyć jako zestaw reguł ustawień regionalnych typu `time_put` \< CharType, OutputIterator >.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class CharType, class OutIt = ostreambuf_iterator<CharType, char_traits<CharType>>>
class time_put_byname : public time_put<CharType, OutputIterator>
{
public:
    explicit time_put_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_put_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_put_byname();

};
```  
  
#### <a name="parameters"></a>Parametry  
 `_Locname`  
 Nazwa ustawień regionalnych.  
  
 `_Refs`  
 Liczba początkowa odwołania.  
  
## <a name="remarks"></a>Uwagi  
 Jego zachowanie jest określany przez [o nazwie](../standard-library/locale-class.md#name) ustawień regionalnych `_Locname`. Każdy Konstruktor inicjuje jego obiektu podstawowego z [time_put —](../standard-library/time-put-class.md#time_put)\<CharType, OutputIterator > ( `_Refs`).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ustawień regionalnych >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



