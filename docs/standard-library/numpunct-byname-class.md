---
title: "numpunct_byname — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xlocnum/std::numpunct_byname
dev_langs:
- C++
helpviewer_keywords:
- numpunct_byname class
ms.assetid: 18412924-e085-4771-b5e9-7a200cbdd7c0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f4ffc167ff6d3afc0dfb972c950a5171cbed20a5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
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



