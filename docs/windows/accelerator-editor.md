---
title: Edytor klawiszy skrótów (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.accelerator.F1
helpviewer_keywords:
- accelerator tables [C++], editing
- tables [C++], accelerator key
- accelerator keys [C++]
- resource editors [C++], Accelerator editor
- keyboard shortcuts [C++], Accelerator editor
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
ms.openlocfilehash: fdb2d9cf0954142da990a0a9f995cb482060345d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621497"
---
# <a name="accelerator-editor-c"></a>Edytor klawiszy skrótów (C++)

Tabeli klawiszy skrótu jest zasób Windows C++, który zawiera listę klawisze skrótów (znany także jako klawisze skrótów) i identyfikatory poleceń, które są skojarzone z nimi. Program może mieć więcej niż jednej tabeli akceleratora.

Zwykle akceleratorów są używane jako skróty klawiaturowe dla poleceń programu, które są również dostępne w menu lub paska narzędzi. Jednak można użyć tabeli akceleratora do definiowania kombinacji klawiszy dla polecenia, które nie mają skojarzonych z nimi obiektu interfejsu użytkownika.

Możesz użyć [Widok klas](/visualstudio/ide/viewing-the-structure-of-code) można dołączyć klucza polecenia klawiszy skrótów do kodu.

Za pomocą **akceleratora** edytora, możesz:

- [Ustawianie właściwości klawiszy skrótów](../windows/setting-accelerator-properties.md)

- [Kojarzenie klawisza skrótu z elementem Menu](../windows/associating-an-accelerator-key-with-a-menu-item.md)

- [Edytowanie tabel akceleratora](../windows/editing-accelerator-tables.md)

- [Użyj wstępnie zdefiniowane klawisze skrótów](../windows/predefined-accelerator-keys.md)

   > [!TIP]
   > Podczas korzystania z **akceleratora** edytora, możesz kliknąć prawym przyciskiem myszy, aby wyświetlić menu skrótów z najczęściej używanymi poleceniami. Dostępne polecenia zależą od tego, wskaźnik wskazuje na.

   > [!NOTE]
   > Windows nie pozwalają na tworzenie tabel akceleratora puste. Jeśli utworzenia tabeli akceleratora żadnych wpisów, zostanie usunięta automatycznie po zapisaniu tabeli.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytory zasobów](../windows/resource-editors.md)