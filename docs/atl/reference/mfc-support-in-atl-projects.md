---
title: Obsługa MFC w projektach ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.addmfc
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d42afec863695b1cab05c2d3cf2f65f3d64a1507
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360644"
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

