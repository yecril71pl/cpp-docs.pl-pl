---
title: Określanie optymalizacji kompilatora dla projektu ATL
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
ms.openlocfilehash: c3b00823cb33be952451c3cc9e370c99140acc3c
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630611"
---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>Określanie optymalizacji kompilatora dla projektu ATL

Domyślnie [Kreator kontrolki ATL](../../atl/reference/atl-control-wizard.md) generuje nowe klasy za pomocą makra ATL_NO_VTABLE w następujący sposób:

```
class ATL_NO_VTABLE CProjName
{
...
};
```

Następnie ATL definiuje _ATL_NO_VTABLE w następujący sposób:

```
#ifdef _ATL_DISABLE_NO_VTABLE
#define ATL_NO_VTABLE
#else
#define ATL_NO_VTABLE __declspec(novtable)
#endif
```

Jeśli nie zdefiniujesz _ATL_DISABLE_NO_VTABLE, makro ATL_NO_VTABLE zostanie rozwinięte do `declspec(novtable)`. Użycie `declspec(novtable)`w deklaracji klasy uniemożliwia zainicjowanie wskaźnika tabeli metod w konstruktorze klas i destruktorze. Podczas kompilowania projektu konsolidator eliminuje tablicę i wszystkie funkcje, do których wskazuje tablicę.

Musisz użyć ATL_NO_VTABLE, a w związku `declspec(novtable)`z tym tylko klasy bazowe, których nie można utworzyć bezpośrednio. `declspec(novtable)` Nie należy używać klasy z klasą pochodną w projekcie, ponieważ ta klasa (zwykle [CComObject](../../atl/reference/ccomobject-class.md), [CComAggObject](../../atl/reference/ccomaggobject-class.md)lub [CComPolyObject](../../atl/reference/ccompolyobject-class.md)) inicjuje wskaźnik tablic wirtualnych dla projektu.

Nie należy wywoływać funkcji wirtualnych z konstruktora dowolnego obiektu, który używa `declspec(novtable)`. Należy przenieść te wywołania do metody [FinalConstruct](ccomobjectrootex-class.md#finalconstruct) .

Jeśli nie masz pewności, czy należy używać `declspec(novtable)` modyfikatora, można usunąć makro ATL_NO_VTABLE z dowolnej definicji klasy lub można je globalnie wyłączyć, określając

```
#define _ATL_DISABLE_NO_VTABLE
```

w pliku *PCH. h* (*stdafx. h* w programie Visual Studio 2017 i starszych) przed uwzględnieniem wszystkich innych plików nagłówkowych ATL.

## <a name="see-also"></a>Zobacz także

[Kreator projektu ATL](../../atl/reference/atl-project-wizard.md)<br/>
[C++typy projektów w programie Visual Studio](../../build/reference/visual-cpp-project-types.md)<br/>
[Programowanie za pomocą kodu ATL i C Run-Time](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Podstawowe informacje na temat obiektów COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[novtable](../../cpp/novtable.md)<br/>
[Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)
