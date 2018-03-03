---
title: "Typy połączeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- no linkage
- linkage [C++], none
- linkage [C++], types of
- types [C++], linkage
- internal linkage, types of linkage
- external linkage, linkage types
ms.assetid: 41326c7f-4602-4bad-a648-697604858ba0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f71fc6e0d0251db38cd1c3dc1032ba6c71ba3ba4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="types-of-linkage"></a>Typy połączeń
Nazwy obiektów i funkcje są wspólne dla jednostki tłumaczenia sposób nosi nazwę połączenie. Te nazwy mogą być:  
  
-   Połączenie wewnętrzne, w którym to przypadku odwoływać się tylko do elementów programu w ich własnych jednostek tłumaczenia; nie są one udostępniane innych jednostek tłumaczenia.  
  
     Tej samej nazwie w innej jednostce tłumaczenia mogą odwoływać się do innego obiektu lub inną klasę. Nazwy z powiązaniem wewnętrznym są czasami określane jako lokalnego do ich jednostek tłumaczenia.  
  
     Deklaracja przykład nazwy z powiązaniem wewnętrznym jest:  
  
    ```  
    static int i;   // The static keyword ensures internal linkage.  
    ```  
  
-   Połączenie zewnętrzne, w którym to przypadku mogą odwoływać się do elementów program w dowolnym jednostce tłumaczenia w programie — program element współużytkowany jednostki tłumaczenia.  
  
     Tej samej nazwie w innej jednostce tłumaczenia jest gwarantowana do odwoływania się do tego samego obiektu lub klasy. Nazwy z zewnętrznym powiązaniem są czasami określane jako globalnego.  
  
     Deklaracja przykład nazwy z zewnętrznym powiązaniem jest:  
  
    ```  
    extern int i;  
    ```  
  
-   Brak połączenia, w którym to przypadku odnoszą się do unikatowe jednostki. Tej samej nazwie w innym zakresie nie może odwoływać się do tego samego obiektu. To wyliczenie. (Należy jednak pamiętać, że można przekazać wskaźnika do obiektu bez połączenia. To sprawia, że obiekt dostępne w innych jednostek tłumaczenia.)  
  
## <a name="see-also"></a>Zobacz też  
 [Program i połączenie](../cpp/program-and-linkage-cpp.md)