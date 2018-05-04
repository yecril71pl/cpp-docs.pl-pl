---
title: Właściwość TypeName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- typename_cpp
dev_langs:
- C++
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6eebf038fbe3e5e18e3f2a1e8e7a2aa2554bf41
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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