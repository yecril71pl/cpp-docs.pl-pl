---
title: Tworzenie biblioteki DLL z samymi zasobami
ms.date: 11/04/2016
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
ms.openlocfilehash: 0d729be60ebec7a37d07fed1d14c4fd5330c7242
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220836"
---
# <a name="creating-a-resource-only-dll"></a>Tworzenie biblioteki DLL z samymi zasobami

Tylko zasoby biblioteki DLL jest biblioteki DLL, która zawiera zasoby, takie jak ikony, mapy bitowe, ciągi i okna dialogowe. Przy użyciu tylko zasoby biblioteki DLL jest dobrym sposobem na udostępnianie tego samego zestawu zasobów w wielu programów. Jest również dobrym sposobem na udostępnianie aplikacji zlokalizowanej w wielu językach zasoby (zobacz [zlokalizowane zasoby w aplikacjach MFC: Biblioteki DLL Satellite](localized-resources-in-mfc-applications-satellite-dlls.md)).

Aby utworzyć bibliotekę DLL tylko do zasobów, Utwórz nowy projekt biblioteki DLL systemu Win32 (inne niż MFC) i Dodaj zasoby do projektu.

- Wybierz projekt systemu Win32 w **nowy projekt** okna dialogowego pole, a następnie określ typ projektu biblioteki DLL w Kreatorze projektu Win32.

- Utwórz nowy skrypt zasobu, który zawiera zasoby (na przykład ciąg lub menu) biblioteki dll i Zapisz plik .rc.

- Na **projektu** menu, kliknij przycisk **Dodaj istniejący element**, a następnie Wstaw nowy plik .rc w projekcie.

- Określ [/noentry](reference/noentry-no-entry-point.md) — opcja konsolidatora. / NOENTRY Zapobiega łączeniu odwołania do konsolidatora `_main` do biblioteki DLL; ta opcja jest wymagana do utworzenia DLL tylko dla zasobów.

- Skompiluj bibliotekę DLL.

Aplikacji, która używa tylko zasoby biblioteki DLL powinny wywoływać [LoadLibrary](loadlibrary-and-afxloadlibrary.md) jawne łącze do biblioteki DLL. Dostęp do zasobów, należy wywołać funkcje ogólne `FindResource` i `LoadResource`, które działają na dowolny rodzaj zasobu lub wywołać jedną z następujących funkcji specyficznych dla zasobów:

- `FormatMessage`

- `LoadAccelerators`

- `LoadBitmap`

- `LoadCursor`

- `LoadIcon`

- `LoadMenu`

- `LoadString`

Aplikacja powinna wywołać `FreeLibrary` po zakończeniu korzystania z zasobów.

## <a name="see-also"></a>Zobacz także

[Praca z plikami zasobów](../windows/working-with-resource-files.md)<br/>
[Tworzenie bibliotek DLL języka C/C++ w programie Visual Studio](dlls-in-visual-cpp.md)
