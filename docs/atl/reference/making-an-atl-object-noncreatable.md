---
title: Tworzenie noncreatable — obiekt ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.objects
dev_langs:
- C++
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf2b3d047a6618326e69dcb51f143f77fc10c8a6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099541"
---
# <a name="making-an-atl-object-noncreatable"></a>Tworzenie noncreatable — obiekt ATL

Atrybuty obiektu COM opartych na ATL można zmienić tak, aby klient nie można bezpośrednio utworzyć obiekt. W tym przypadku obiekt będzie można zwracany przez wywołanie metody na innym obiekcie zamiast bezpośrednio tworzone.

### <a name="to-make-an-object-noncreatable"></a>Zapewnienie noncreatable — obiekt

1. Usuń [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) dla obiektu. Obiekt noncreatable — ale formant do zarejestrowania, Zamień OBJECT_ENTRY_AUTO z [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto).

2. Dodaj [noncreatable —](../../windows/noncreatable.md) atrybutu klasy coclass w pliku .idl. Na przykład:

    ```  
    [uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851), 
    helpstring("MyObject"), 
    noncreatable]  
    coclass MyObject  
    {  
        [default] interface IMyInterface;  
    }  
    ```

## <a name="see-also"></a>Zobacz też

[Kreator projektu ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Typy projektów Visual C++](../../ide/visual-cpp-project-types.md)<br/>
[Tworzenie projektów wykorzystujących interfejs Pulpitu za pomocą kreatorów aplikacji](../../ide/creating-desktop-projects-by-using-application-wizards.md)<br/>
[Programowanie za pomocą kodu ATL i C Run-Time](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Podstawowe informacje na temat obiektów COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)

