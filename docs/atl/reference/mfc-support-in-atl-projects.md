---
title: Obsługa MFC w projektach ATL
ms.date: 11/04/2016
f1_keywords:
- vc.atl.addmfc
helpviewer_keywords:
- ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
ms.openlocfilehash: 0aece6805f1de987b0164f405e50b99fd706fef4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275428"
---
# <a name="mfc-support-in-atl-projects"></a>Obsługa MFC w projektach ATL

Jeśli wybierzesz **obsługi MFC** w Kreatorze projektu ATL projektu deklaruje aplikacji jako obiekt aplikacji MFC (klasy). Projekt inicjuje biblioteki MFC i tworzy wystąpienia klasy (klasy *ProjName*) który jest tworzony na podstawie [CWinApp](../../mfc/reference/cwinapp-class.md).

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

Możesz wyświetlić klasę obiektu aplikacji i jej `InitInstance` i `ExitInstance` funkcji w widoku klas.

## <a name="see-also"></a>Zobacz także

[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)
