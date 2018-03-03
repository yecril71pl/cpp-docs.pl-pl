---
title: "Określanie Optymalizacja kompilatora Projekt ATL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
dev_langs:
- C++
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6e60f22b7b91567948dfc2efc90935fce266d7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>Określanie Optymalizacja kompilatora Projekt ATL
Domyślnie [Kreator formantu ATL](../../atl/reference/atl-control-wizard.md) generuje nowe klasy z makra ATL_NO_VTABLE w następujący sposób:  
  
```  
class ATL_NO_VTABLE CProjName  
{  
 ...  
};  
```  
  
 ATL definiuje _ATL_NO_VTABLE w następujący sposób:  
  
```  
#ifdef _ATL_DISABLE_NO_VTABLE  
 #define ATL_NO_VTABLE  
#else  
 #define ATL_NO_VTABLE __declspec(novtable)  
#endif  
```  
  
 Jeśli nie zostanie zdefiniowana _ATL_DISABLE_NO_VTABLE, makro ATL_NO_VTABLE rozwijany do `declspec(novtable)`. Przy użyciu `declspec(novtable)`w klasie deklaracji uniemożliwia wskaźnikiem vtable inicjowanej w klasie Konstruktor i destruktor. Podczas kompilowania projektu konsolidator eliminuje vtable i wszystkie funkcje, które wskazuje vtable.  
  
 Należy użyć ATL_NO_VTABLE i w związku z tym `declspec(novtable)`, z tylko klas podstawowych, które nie są bezpośrednio możliwość utworzenia. Nie można używać `declspec(novtable)` w klasie pochodnej większość w projekcie, ponieważ ta klasa (zazwyczaj [element CComObject](../../atl/reference/ccomobject-class.md), [CComAggObject](../../atl/reference/ccomaggobject-class.md), lub [CComPolyObject](../../atl/reference/ccompolyobject-class.md)) Inicjuje wskaźnikiem vtable dla projektu.  
  
 Nie należy wywołać funkcji wirtualnych z konstruktora dowolnego obiektu, który używa `declspec(novtable)`. Należy przenieść tych wywołań [FinalConstruct](ccomobjectrootex-class.md#finalconstruct) metody.  

  
 Jeśli nie wiesz, czy należy używać `declspec(novtable)` modyfikator, możesz usunąć makro ATL_NO_VTABLE z żadnych definicji klasy lub można globalnie ją wyłączyć, określając  
  
```  
#define _ATL_DISABLE_NO_VTABLE  
```  
  
 w pliku stdafx.h przed wszystkie inne ATL pliki nagłówka są dołączone.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator projektu ATL](../../atl/reference/atl-project-wizard.md)   
 [Typy projektów Visual C++](../../ide/visual-cpp-project-types.md)   
 [Tworzenie projektów pulpitu za pomocą kreatorów aplikacji](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Programowanie za pomocą ALT i C Run-Time kodu](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Podstawowe informacje na temat ATL COM — obiekty](../../atl/fundamentals-of-atl-com-objects.md)   
 [novtable](../../cpp/novtable.md)   
 [Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)

