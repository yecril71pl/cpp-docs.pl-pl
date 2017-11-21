---
title: '&lt;Lista&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- list
- <list>
dev_langs: C++
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0d7b4e97cb5e14bb50b914f883fdd5237afa5496
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltlistgt-visual-c"></a>&lt;Lista&gt; (Visual C++)
\<Listheader > Blok służy do definiowania wiersz nagłówka tabeli lub definicji listy. Podczas definiowania tabeli, wystarczy podać wpis termin w nagłówku.  
  
## <a name="syntax"></a>Składnia  
  
```  
<list type="bullet" | "number" | "table">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### <a name="parameters"></a>Parametry  
 `term`  
 Termin, aby zdefiniować, który zostanie zdefiniowany w `description`.  
  
 `description`  
 Element punktora lub Lista numerowana definicji `term`.  
  
## <a name="remarks"></a>Uwagi  
 Każdy element na liście zostanie określony z \<elementu > bloku. Podczas tworzenia listy definicji, należy określić zarówno `term` i `description`. Jednak dla tabeli, lista punktowana lub Lista numerowana, tylko należy podać wpis dotyczący `description`.  
  
 Listy lub tabeli może mieć tyle \<elementu > blokuje zgodnie z potrzebami.  
  
 Kompiluj z użyciem [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
  
```  
// xml_list_tag.cpp  
// compile with: /doc /LD  
// post-build command: xdcmake xml_list_tag.dll  
/// <remarks>Here is an example of a bulleted list:  
/// <list type="bullet">  
/// <item>  
/// <description>Item 1.</description>  
/// </item>  
/// <item>  
/// <description>Item 2.</description>  
/// </item>  
/// </list>  
/// </remarks>  
class MyClass {};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Plik dokumentacji XML](../ide/xml-documentation-visual-cpp.md)