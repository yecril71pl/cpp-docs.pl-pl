---
title: "numpunct_byname — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xlocnum/std::numpunct_byname
dev_langs: C++
helpviewer_keywords: numpunct_byname class
ms.assetid: 18412924-e085-4771-b5e9-7a200cbdd7c0
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d73e5835d0b3b8e871afe4a9d61765c479d20adc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="numpunctbyname-class"></a>numpunct_byname — Klasa
Klasy pochodne szablonu opisuje obiekt, który może służyć jako `numpunct` aspektu danego ustawień regionalnych włączenie formatowanie i znaki interpunkcyjne wyrażeń liczbowych i logicznych.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class CharType>
class numpunct_byname : public numpunct<Elem> {
public:
    explicit numpunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit numpunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~numpunct_byname();

 };
```  
  
## <a name="remarks"></a>Uwagi  
 Jego zachowanie jest określany przez [o nazwie](../standard-library/locale-class.md#name) ustawień regionalnych `_Locname`. Konstruktor inicjuje jego obiektu podstawowego z [numpunct —](../standard-library/numpunct-class.md#numpunct)\<CharType > ( `_Refs`).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ustawień regionalnych >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



