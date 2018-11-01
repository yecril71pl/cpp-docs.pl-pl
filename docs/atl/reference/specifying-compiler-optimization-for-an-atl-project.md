---
title: Określanie optymalizacji kompilatora dla projektu ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
ms.openlocfilehash: 18c1f404576a7e011698f0b553a2436bab8089a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522304"
---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>Określanie optymalizacji kompilatora dla projektu ATL

Domyślnie [Kreator kontrolki ATL](../../atl/reference/atl-control-wizard.md) generuje nowych klas przy użyciu makra ATL_NO_VTABLE w następujący sposób:

```
class ATL_NO_VTABLE CProjName
{
...
};
```

ATL definiuje następnie _ATL_NO_VTABLE w następujący sposób:

```
#ifdef _ATL_DISABLE_NO_VTABLE
#define ATL_NO_VTABLE
#else
#define ATL_NO_VTABLE __declspec(novtable)
#endif
```

Jeżeli nie zdefiniujesz _ATL_DISABLE_NO_VTABLE, makro ATL_NO_VTABLE rozwija `declspec(novtable)`. Za pomocą `declspec(novtable)`w klasie deklaracji zapobiega wskaźnika vtable inicjowanego w konstruktorze klasy i destruktor. Podczas tworzenia projektu, konsolidator eliminuje vtable i wszystkie funkcje, na które wskazuje vtable.

Należy użyć ATL_NO_VTABLE i w związku z tym `declspec(novtable)`, za pomocą tylko klas bazowych, które nie są bezpośrednio możliwe do utworzenia. Nie można używać `declspec(novtable)` najbardziej pochodnego klasą w projekcie, ponieważ ta klasa (zazwyczaj [CComObject](../../atl/reference/ccomobject-class.md), [CComAggObject](../../atl/reference/ccomaggobject-class.md), lub [CComPolyObject](../../atl/reference/ccompolyobject-class.md)) Inicjuje wskaźnika vtable dla Twojego projektu.

Nie należy wywołać funkcji wirtualnych z konstruktora dowolnego obiektu, który używa `declspec(novtable)`. Należy przenieść te wywołania [FinalConstruct](ccomobjectrootex-class.md#finalconstruct) metody.

Jeśli wiesz, czy należy używać `declspec(novtable)` modyfikator, możesz usunąć makro ATL_NO_VTABLE z dowolnego poziomu definicji klasy lub globalnie można ją wyłączyć, określając

```
#define _ATL_DISABLE_NO_VTABLE
```

w pliku stdafx.h przed wszystkie inne ATL nagłówka dołączane są pliki.

## <a name="see-also"></a>Zobacz też

[Kreator projektu ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Typy projektów Visual C++](../../ide/visual-cpp-project-types.md)<br/>
[Tworzenie projektów wykorzystujących interfejs Pulpitu za pomocą kreatorów aplikacji](../../ide/creating-desktop-projects-by-using-application-wizards.md)<br/>
[Programowanie za pomocą kodu ATL i C Run-Time](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Podstawowe informacje na temat obiektów COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[novtable](../../cpp/novtable.md)<br/>
[Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)

