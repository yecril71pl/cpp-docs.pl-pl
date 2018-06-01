---
title: '&lt;Lista&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- list
- <list>
dev_langs:
- C++
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bff8e3588e31414f50cb6d150c0e8c9f2603586b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "33323982"
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
 [Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)