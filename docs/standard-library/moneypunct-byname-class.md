---
title: "moneypunct_byname — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xlocmon/std::moneypunct_byname
dev_langs:
- C++
helpviewer_keywords:
- moneypunct_byname class
ms.assetid: e8a544d2-6aee-420d-b513-deb385c9b416
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d50e841af6ca158e431d29bf6a139fd9534748bd
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="moneypunctbyname-class"></a>moneypunct_byname — Klasa
Klasy pochodne szablonu, która opisuje obiekt, który może służyć jako `moneypunct` aspektu danego ustawienia regionalne, włączanie pieniężnego formatowania danych wejściowych pól pieniężnego danych wyjściowych.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class CharType, bool Intl = false>
class moneypunct_byname : public moneypunct<CharType, Intl>
{
public:
    explicit moneypunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit moneypunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~moneypunct_byname();

};
```  
  
## <a name="remarks"></a>Uwagi  
 Jego zachowanie jest określany przez nazwany ustawień regionalnych `_Locname`. Każdy Konstruktor inicjuje jego obiektu podstawowego z [moneypunct —](../standard-library/moneypunct-class.md#moneypunct)\<CharType, wewnętrzna > ( `_Refs`).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ustawień regionalnych >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



