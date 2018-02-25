---
title: "&lt;allocators —&gt; makra | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/std::ALLOCATOR_DECL
- allocators/std::CACHE_CHUNKLIST
- allocators/std::CACHE_FREELIST
- allocators/std::CACHE_SUBALLOC
- allocators/std::SYNC_DEFAULT
ms.assetid: 9cb5ee07-1ff9-4594-ae32-3c8c6efb511a
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::ALLOCATOR_DECL [C++]
- std::CACHE_CHUNKLIST [C++]
- std::CACHE_FREELIST [C++]
- std::CACHE_SUBALLOC [C++]
- std::SYNC_DEFAULT [C++]
ms.openlocfilehash: 7bd292ee2c19c2db90f126d6082854141c3e71fc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltallocatorsgt-macros"></a>&lt;allocators —&gt; makra
||||  
|-|-|-|  
|[ALLOCATOR_DECL](#allocator_decl)|[CACHE_CHUNKLIST](#cache_chunklist)|[CACHE_FREELIST](#cache_freelist)|  
|[CACHE_SUBALLOC](#cache_suballoc)|[SYNC_DEFAULT](#sync_default)|  
  
##  <a name="allocator_decl"></a>  ALLOCATOR_DECL —  
 Daje alokatora klasy szablonu.  
  
```
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```  
  
### <a name="remarks"></a>Uwagi  
 Makro daje definicji szablonu `template <class Type> class name {.....}` i specjalizacji `template <> class name<void> {.....}` definiującą razem Allocator — klasa szablonu, który używa filtr synchronizacji `sync` i pamięci podręcznej typu `cache`.  
  
 Dla kompilatorów, które można skompilować ponownie Utwórz wiązanie wynikowy definicji szablonu wygląda następująco:  
```  
struct rebind
   {    /* convert a name<Type> to a name<Other> */
   typedef name<Other> other;
   };  
 ```  
 Dla kompilatory, nie można skompilować ponownie Utwórz wiązanie, wynikowy definicji szablonu wygląda następująco:  
  
```
template <class Type<class name
    : public stdext::allocators::allocator_base<Type,
    sync<stdext::allocators::rts_alloc<cache>>>
{
public:
    name() {}
    template <class Other>
    name(const name<Other>&) {}
    template <class Other>
    name& operator= (const name<Other>&)
    {
        return *this;
    }
};
```  
  
##  <a name="cache_chunklist"></a>  CACHE_CHUNKLIST —  
 Daje `stdext::allocators::cache_chunklist<sizeof(Type)>`.  
  
```
#define CACHE_CHUNKLIST <cache_class>
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="cache_freelist"></a>  CACHE_FREELIST —  
 Daje `stdext::allocators::cache_freelist<sizeof(Type), max>`.  
  
```
#define CACHE_FREELIST(max) <cache_class>
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="cache_suballoc"></a>  CACHE_SUBALLOC  
 Daje `stdext::allocators::cache_suballoc<sizeof(Type)>`.  
  
```
#define CACHE_SUBALLOC <cache_class>
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="sync_default"></a>  SYNC_DEFAULT  
 Daje filtr synchronizacji.  
  
```
#define SYNC_DEFAULT <sync_template>
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli kompilatora obsługuje kompilowania zarówno jednowątkowe i wielowątkowe aplikacje, dla aplikacji jednowątkowych makro daje `stdext::allocators::sync_none`; we wszystkich innych przypadkach go daje `stdext::allocators::sync_shared`.  
  
## <a name="see-also"></a>Zobacz też  
 [\<allocators>](../standard-library/allocators-header.md)




