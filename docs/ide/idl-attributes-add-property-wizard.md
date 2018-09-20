---
title: Atrybuty IDL, Kreator dodawania właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.prop.idlattributes
dev_langs:
- C++
ms.assetid: 356ed666-79d0-4bd9-a5e7-cda679cbadbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce3597f656d46da85faee3f6ec51b89257d25d05
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426357"
---
# <a name="idl-attributes-add-property-wizard"></a>Atrybuty IDL, Dodaj kreatora właściwości

Ta strona kreatora dodawania właściwości umożliwia Określ jakiekolwiek ustawienia interfejsu definicja języka (IDL) dla właściwości.

- **id**

   Określa numeryczny identyfikator, który identyfikuje właściwość. Ta opcja nie jest dostępne dla właściwości niestandardowych interfejsów. Zobacz [identyfikator](/windows/desktop/Midl/id) w *odwołania MIDL*.

- **helpcontext**

   Określa identyfikator kontekstu, który pozwala użytkownikowi oglądać informacje o tej właściwości w pliku pomocy. Zobacz [helpcontext —](/windows/desktop/Midl/helpcontext) w *odwołania MIDL*.

- **helpstring**

   Określa ciąg znaków, który jest używany do opisania elementu, do której jest stosowany. Domyślnie jest ustawiona "właściwość *nazwa właściwości*." Zobacz [HelpString —](/windows/desktop/Midl/helpstring) w *odwołania MIDL*.

## <a name="other-options"></a>Inne opcje

Nie wszystkie opcje są dostępne dla wszystkich typów właściwości.

|Opcja|Opis|
|------------|-----------------|
|**bindable**|Wskazuje, że właściwość obsługuje powiązanie danych. Zobacz [możliwej do wiązania](/windows/desktop/Midl/bindable) w *odwołania MIDL*. Wykonania akcji właściwość ta opcja jest ustawiana domyślnie i można zmienić.|
|**defaultbind**|Wskazuje, że pojedynczy, które można powiązać właściwości najlepsze jest to obiekt. Zobacz [defaultbind —](/windows/desktop/Midl/defaultbind) w *odwołania MIDL*.|
|**displaybind**|Wskazuje, że ta właściwość powinna być wyświetlana użytkownikowi jak możliwa do powiązania. Zobacz [displaybind —](/windows/desktop/Midl/displaybind) w *odwołania MIDL*.|
|**immediatebind**|Wskazuje, że baza danych zostanie niezwłocznie powiadomiona o wszystkich zmianach tej właściwości obiektów powiązanych z danymi. Zobacz [immediatebind —](/windows/desktop/Midl/immediatebind) w *odwołania MIDL*.|
|**defaultcollelem**|Wskazuje, że właściwość jest funkcję dostępu do elementu domyślnej kolekcji. Zobacz [defaultcollelem —](/windows/desktop/Midl/defaultcollelem) w *odwołania MIDL*.|
|**nonbrowsable**|Tagi interfejsu lub dispinterface elementu członkowskiego, który nie powinien być wyświetlany w przeglądarce właściwości. Zobacz [nonbrowsable —](/windows/desktop/Midl/nonbrowsable) w *odwołania MIDL*.|
|**requestedit**|Wskazuje, że właściwość obsługuje **OnRequestEdit** powiadomień zobacz [requestedit —](/windows/desktop/Midl/requestedit) w *odwołania MIDL*. Wykonania akcji właściwość ta opcja jest ustawiana domyślnie i można zmienić.|
|**source**|Wskazuje, że jest członkiem właściwość jest źródłem zdarzeń. Zobacz [źródła](/windows/desktop/Midl/source) w *odwołania MIDL*.|
|**hidden**|Wskazuje, że właściwość istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika. Zobacz [ukryte](/windows/desktop/Midl/hidden) w *odwołania MIDL*.|
|**restricted**|Określa, że właściwość nie może być wywoływana arbitralnie. Zobacz [ograniczeniami](/windows/desktop/Midl/restricted) w *odwołania MIDL*.|
|`local`|Określa kompilatorowi MIDL, właściwość nie jest zdalny. Zobacz [lokalnego](/windows/desktop/Midl/local) w *odwołania MIDL*.|

## <a name="see-also"></a>Zobacz też

[Dodawanie właściwości](../ide/adding-a-property-visual-cpp.md)<br>
[Nazwy, Kreator dodawania właściwości](../ide/names-add-property-wizard.md)<br>
[Implementowanie interfejsu](../ide/implementing-an-interface-visual-cpp.md)<br>
[Właściwości podstawowe](../ide/stock-properties.md)