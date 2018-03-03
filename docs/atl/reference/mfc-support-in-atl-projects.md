---
title: "Obsługa MFC w projektach ATL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.atl.addmfc
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 399f9fcea216adf5480bf38b8aba051c60eed496
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-support-in-atl-projects"></a>Obsługa MFC w projekty ATL
W przypadku wybrania **Obsługa MFC** w Kreatorze projektu ATL projektu deklaruje aplikacji jako obiekt aplikacji MFC (klasa). Inicjuje biblioteki MFC i tworzy wystąpienie klasy projektu (klasa *nazwa_projektu.nazwa_modułu.nazwa_procedury*) która jest pochodną [CWinApp](../../mfc/reference/cwinapp-class.md).  
  
 Ta opcja jest dostępna dla nonattributed projektów ATL DLL.  
  
```  
class CProjNameApp : public CWinApp  
{  
public:  
 
// Overrides  
    virtual BOOL InitInstance();
virtual int ExitInstance();
DECLARE_MESSAGE_MAP() 
};  
 
BEGIN_MESSAGE_MAP(CProjNameApp, CWinApp)  
END_MESSAGE_MAP()  
 
CProjNameApp theApp;  
 
BOOL CProjNameApp::InitInstance()  
{  
    return CWinApp::InitInstance();

}  
 
int CProjNameApp::ExitInstance()  
{  
    return CWinApp::ExitInstance();

}  
```  
  
 Możesz wyświetlić klasę obiektu aplikacji i jej `InitInstance` i `ExitInstance` funkcji w widoku klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)   
 [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)   
 [Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)

