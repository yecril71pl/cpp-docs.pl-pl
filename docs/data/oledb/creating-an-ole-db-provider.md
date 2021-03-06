---
title: Tworzenie dostawcy OLE DB
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
ms.openlocfilehash: 3e46e87b0d5d538a0f9fd7e231debfef3fa95210
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361896"
---
# <a name="creating-an-ole-db-provider"></a>Tworzenie dostawcy OLE DB

Zalecany sposób tworzenia dostawcy OLE DB jest za pomocą kreatorów, aby utworzyć Projekt ATL COM i dostawcy, a następnie zmodyfikuj pliki przy użyciu szablonów OLE DB. Podczas dostosowywania dostawcy można przekształcić w komentarz zbędne właściwości i dodać opcjonalne interfejsy.

Podstawowe kroki są następujące:

1. Użyj **Kreator projektów ATL** do tworzenia plików podstawowego projektu i **Kreator dostawcy interfejsu OLE DB ATL** do utworzenia dostawcy (wybierz **dostawcy OLE DB ATL** z **Zainstalowane** > **Visual C++** > **ATL** folderu w **Dodaj nowy element**).

   > [!NOTE]
   > Projekt musi zawierać obsługę MFC przed dodaniem **dostawcy OLE DB ATL**.

1. Zmodyfikuj kod `Execute` method in Class metoda [CCustomRowset(CustomRS.h)](cmyproviderrowset-myproviderrs-h.md). Aby uzyskać przykład, zobacz [odczyt ciągów do dostawcy OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).

1. Edytuj właściwości mapy w [CustomDS.h](cmyprovidersource-myproviderds-h.md), [CustomSess.h](cmyprovidersession-myprovidersess-h.md), i [CustomRS.h](cmyproviderrowset-myproviderrs-h.md). Kreator utworzy map właściwości, które zawierają wszystkie właściwości, które mogą zaimplementować dostawcę. Przejdź do mapy właściwości i usuń lub komentarz właściwości, które Twój dostawca musi obsługiwać.

1. Aktualizuj PROVIDER_COLUMN_MAP, w którym znajdują się w [CCustomRowset(CustomRS.h)](cmyproviderrowset-myproviderrs-h.md). Aby uzyskać przykład, zobacz [przechowywanie ciągów w dostawcy OLE DB](../../data/oledb/storing-strings-in-the-ole-db-provider.md).

1. Gdy wszystko jest gotowe do testowania dostawcy, można ją przetestować, próbując znaleźć dostawcy w wyliczeniu dostawcy. Aby zapoznać się z przykładami kodu, który umożliwia znalezienie dostawcy w wyliczeniu, zobacz [CATDB](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb) i [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer) próbek lub w przykładzie w [Implementowanie prostego konsumenta](../../data/oledb/implementing-a-simple-consumer.md).

1. Dodaj wszelkie dodatkowe interfejsy, które chcesz. Aby uzyskać przykład, zobacz [udoskonalanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md).

   > [!NOTE]
   > Domyślnie kreatorów wygenerować kod, który jest poziom OLE DB 0 zgodne. Aby upewnić się, że aplikacja pozostanie poziom 0 jest zgodne, nie usuwaj żadnego z interfejsów generowane przez kreatora z kodu.

## <a name="see-also"></a>Zobacz także

[Przykład CatDB: Data Source Schema Browser](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb)<br/>
[Przykład DBViewer: Przeglądarka bazy danych](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer)
