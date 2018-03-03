---
title: "Właściwość TypeName | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- typename_cpp
dev_langs:
- C++
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a276d13172b675cc6856e726cd7139e36fa97d41
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="typename"></a>typename
W definicji szablonu stanowi wskazówkę kompilator że typem jest nieznany identyfikator. W polu listy parametrów szablonu służy do określania parametrów typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
typename identifier;  
```  
  
## <a name="remarks"></a>Uwagi  
 To słowo kluczowe należy użyć, jeśli nazwa w definicji szablonu jest kwalifikowana nazwa, która jest zależna od argumentu szablonu; jest opcjonalne, jeśli nazwa kwalifikowana nie jest zależne. Aby uzyskać więcej informacji, zobacz [szablony i rozpoznawanie nazw](../cpp/templates-and-name-resolution.md).  
  
 **Właściwość TypeName** mogą być używane przez dowolnego typu, w dowolnym miejscu szablonu deklaracji lub definicji. Nie są dozwolone w liście klas podstawowych, chyba że jako argument szablonu do szablonu klasy podstawowej.  
  
```  
template <class T>  
class C1 : typename T::InnerType // Error - typename not allowed.  
{};  
template <class T>  
class C2 : A<typename T::InnerType>  // typename OK.  
{};  
```  
  
 **Typename** można również użyć słowa kluczowego zamiast **klasy** parametr szablonu na liście. Na przykład semantycznie równoważne są następujące instrukcje:  
  
```  
template<class T1, class T2>...  
template<typename T1, typename T2>...  
```  
  
## <a name="example"></a>Przykład  
  
```  
// typename.cpp  
template<class T> class X  
{  
   typename T::Y m_y;   // treat Y as a type  
};  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony](../cpp/templates-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)