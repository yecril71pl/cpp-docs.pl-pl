---
title: "collate_byname — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: locale/std::collate_byname
dev_langs: C++
helpviewer_keywords: collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 03a043e26aabde7e985c53dd33900f2ca1926487
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="collatebyname-class"></a>collate_byname — Klasa
Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł sortowania danych ustawień regionalnych, umożliwiając pobieranie informacji specyficznych dla obszaru kulturowego dotyczących konwencji sortowania ciągów.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class CharType>
class collate_byname : public collate<CharType> {
public:
    explicit collate_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit collate_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~collate_byname();

};
```  
  
#### <a name="parameters"></a>Parametry  
 `_Locname`  
 Nazwane ustawień regionalnych.  
  
 `_Refs`  
 Liczba początkowa odwołania.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt, który może służyć jako opis klasy szablonu [aspektu ustawień regionalnych](../standard-library/locale-class.md#facet_class) typu [collate](../standard-library/collate-class.md#collate)\<CharType >. Jego zachowanie jest określany przez [o nazwie](../standard-library/locale-class.md#name) ustawień regionalnych `_Locname`. Każdy Konstruktor inicjuje jego obiektu podstawowego z [collate](../standard-library/collate-class.md#collate)\<CharType > ( `_Refs`).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ustawień regionalnych >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



