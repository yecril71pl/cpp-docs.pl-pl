---
title: Tworzenie noncreatable — obiekt ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.objects
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
ms.openlocfilehash: da1d5c43d86d95d7eff9b6830b83b61737d3030f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267072"
---
# <a name="making-an-atl-object-noncreatable"></a>Tworzenie noncreatable — obiekt ATL

Atrybuty obiektu COM opartych na ATL można zmienić tak, aby klient nie można bezpośrednio utworzyć obiekt. W tym przypadku obiekt będzie można zwracany przez wywołanie metody na innym obiekcie zamiast bezpośrednio tworzone.

## <a name="to-make-an-object-noncreatable"></a>Zapewnienie noncreatable — obiekt

1. Usuń [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) dla obiektu. Obiekt noncreatable — ale formant do zarejestrowania, Zamień OBJECT_ENTRY_AUTO z [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto).

1. Dodaj [noncreatable —](../../windows/noncreatable.md) atrybutu klasy coclass w pliku .idl. Na przykład:

    ```
    [uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851),
    helpstring("MyObject"),
    noncreatable]
    coclass MyObject
    {
        [default] interface IMyInterface;
    }
    ```

## <a name="see-also"></a>Zobacz także

[Kreator projektu ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Typy projektów Visual C++](../../ide/visual-cpp-project-types.md)<br/>
[Tworzenie projektów wykorzystujących interfejs Pulpitu za pomocą kreatorów aplikacji](../../ide/creating-desktop-projects-by-using-application-wizards.md)<br/>
[Programowanie za pomocą kodu ATL i C Run-Time](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Podstawowe informacje na temat obiektów COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)
