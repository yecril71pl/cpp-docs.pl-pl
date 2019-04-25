---
title: Ciągi szablonu dokumentu, kreator dodawania klas MFC
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.mfc.simple.doctemp
helpviewer_keywords:
- MFC Add Class Wizard, document control strings
ms.assetid: 14e1c834-5e79-4dbd-811f-ec8f0a9cdcb2
ms.openlocfilehash: de0b483b6b3d242ee05680c47ae29ed675d54a36
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322428"
---
# <a name="document-template-strings-mfc-add-class-wizard"></a>Ciągi szablonu dokumentu, kreator dodawania klas MFC

Ta strona kreatora jest dostępna tylko dla klas, które spełniają następujące kryteria:

- Projekt MFC obsługuje architektury dokument/widok.

- Klasa bazowa dla nowej klasy jest [CFormView](../../mfc/reference/cformview-class.md).

- Pole wyboru **zasobów Generowanie tym** jest sprawdzane na **nazwy** części [Kreator klas MFC](../../mfc/reference/mfc-add-class-wizard.md).

Kreator wyświetla ustawienia domyślne dla następujących wartości do projektu widoku formularzy, zarządzania i lokalizacji. Ponieważ większość ciągi szablonu dokumentu są widoczne i używane przez użytkowników formularza, są one zlokalizowane w **język zasobów** czcionką [typy aplikacji](../../mfc/reference/application-type-mfc-application-wizard.md) strony Kreatora aplikacji MFC Podczas tworzenia projektu.

> [!NOTE]
>  Kreator nie zapewnia automatyczna obsługa drukowania dla klasy pochodne `CFormView`.

Zobacz [szablonów dokumentów i proces tworzenia dokumentu/widoku](../../mfc/document-templates-and-the-document-view-creation-process.md) Aby uzyskać więcej informacji.

## <a name="nonlocalized-strings"></a>Niezlokalizowanej ciągów

Ma zastosowanie do aplikacji, które tworzą dokumentów użytkownika. Użytkownicy mogą otwierania i zapisywania dokumentów więcej łatwo Jeśli typ dokumentu ma rozszerzenie pliku i identyfikator typu pliku Te elementy nie są lokalizowane, ponieważ są one używane przez system, a nie przez użytkownika.

- **Rozszerzenie pliku**

   Określa rozszerzenie pliku skojarzone z typem dokumentu dla tej aplikacji formularzy. Domyślne rozszerzenie pliku na podstawie nazwy klasy. Na przykład, jeśli nosi nazwę nowej klasy MFC `CWidget`, domyślnie jest rozszerzenie pliku. wid. Rozszerzenie pliku jest używane w filtrach plików i **Otwórz** i **Zapisz jako** okien dialogowych.

   Jeśli zmienisz rozszerzenie pliku, zmiany są widoczne w **nazwy filtru** pole.

   > [!NOTE]
   > Jeśli zmienisz domyślne rozszerzenie pliku, nie dołączaj okresu.

- **Identyfikator typu pliku**

   Ustawia etykietę dla danego typu dokumentu w rejestrze systemowym.

## <a name="localized-strings"></a>Zlokalizowane ciągi

Tworzy ciągi skojarzone z formularzami i dokumenty, które odczytują i używane przez użytkowników aplikacji, dzięki czemu są zlokalizowane ciągi.

- **Nazwa typu dokumentu**

   Identyfikuje typ dokumentu, w którym mogą być grupowane dokumentu aplikacji. Domyślnie jest on oparty na nazwę klasy. Na przykład, jeśli nosi nazwę nowej klasy MFC **CWidget**, domyślnie, nazwa typu dokumentu jest element Widget. Zmienianie domyślnego nie powoduje zmiany innych opcji, w tym oknie dialogowym.

- **Nazwa filtru**

   Ustawia nazwę, na który użytkownicy mogą wskazać do wyszukiwania plików określonego typu pliku. Ta opcja jest dostępna z **pliki typu** i **Zapisz jako typ** opcje w standardowych Windows **Otwórz** i **Zapisz jako** okien dialogowych. Domyślnie nazwa opiera się na nazwę projektu, a także plików, a następnie rozszerzenia wskazane w **rozszerzenie pliku**. Na przykład, jeśli projekt nosi nazwę elementu Widget i rozszerzenie pliku jest .wid **nazwy filtru** jest element Widget plików (*.wid) domyślnie.

- **Krótka nazwa nowego pliku**

   Ustawia nazwę w standardowych Windows **New** okno dialogowe, jeśli projekt zawiera więcej niż jeden szablon dokumentu. Jeśli aplikacja jest [serwer automatyzacji](../../mfc/automation-servers.md), ta nazwa jest używana jako krótka nazwa obiektu automatyzacji. Domyślnie ta nazwa opiera się na nazwę klasy.

- **Długa nazwa typu pliku**

   Ustawia nazwę typu pliku w rejestrze systemowym. Jeśli aplikacja serwera automatyzacji, ta nazwa jest używana jako długa nazwa obiektu automatyzacji. Domyślnie ta nazwa opiera się na nazwę klasy znaku plus. Dokument. Na przykład, jeśli nazwa klasy jest `CWidget`, **długa nazwa typ pliku** jest dokumentem elementu Widget.

- **Klasy dokumentów**

   Wskazuje, klasa dokumentów projektu. Domyślnie ta klasa jest klasa dokumentu aplikacji głównej, zgodnie z zaleceniami z [przeglądu wygenerowane klasy](../../mfc/reference/generated-classes-mfc-application-wizard.md) strony Kreatora aplikacji MFC. Po dodaniu innych klas dokumentu w projekcie, możesz wybrać inną klasę dokumentu z listy.

## <a name="see-also"></a>Zobacz także

[Kreator dodawania klasy MFC](../../mfc/reference/mfc-add-class-wizard.md)<br/>
[MFC Class](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)
