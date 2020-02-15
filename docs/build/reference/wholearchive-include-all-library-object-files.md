---
title: /WHOLEARCHIVE (Dołącz wszystkie pliki obiektów biblioteki)
ms.date: 02/12/2020
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
ms.openlocfilehash: 95685c9c0dfde45c42449bbcad67228a0e21b36a
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257536"
---
# <a name="wholearchive-include-all-library-object-files"></a>/WHOLEARCHIVE (Dołącz wszystkie pliki obiektów biblioteki)

Wymuś dołączenie wszystkich plików obiektów do biblioteki statycznej w połączonym pliku wykonywalnym.

## <a name="syntax"></a>Składnia

> **/WHOLEARCHIVE**\
> **/WHOLEARCHIVE:** _Biblioteka_

### <a name="arguments"></a>Argumenty

\ *biblioteki*
Opcjonalna nazwa ścieżki do biblioteki statycznej. Konsolidator obejmuje każdy plik obiektu z tej biblioteki.

## <a name="remarks"></a>Uwagi

Opcja/WHOLEARCHIVE wymusza, aby konsolidator zawierał każdy plik obiektu z określonej biblioteki statycznej lub jeśli żadna biblioteka nie została określona, ze wszystkich bibliotek statycznych określonych dla polecenia LINK. Aby określić opcję/WHOLEARCHIVE dla wielu bibliotek, można użyć więcej niż jednego przełącznika/WHOLEARCHIVE w wierszu polecenia konsolidatora. Domyślnie konsolidator zawiera pliki obiektów w połączonych danych wyjściowych tylko wtedy, gdy eksportują symbole przywoływane przez inne pliki obiektów w pliku wykonywalnym. Opcja/WHOLEARCHIVE sprawia, że konsolidator traktuje wszystkie pliki obiektów zarchiwizowane w bibliotece statycznej, tak jakby były one określone pojedynczo w wierszu polecenia konsolidatora.

Opcji/WHOLEARCHIVE można użyć, aby ponownie wyeksportować wszystkie symbole z biblioteki statycznej. Dzięki temu można upewnić się, że podczas tworzenia składnika z więcej niż jednej biblioteki statycznej jest uwzględniany cały kod biblioteki, zasoby i metadane. Jeśli widzisz LNK4264 ostrzegawczy podczas tworzenia biblioteki statycznej zawierającej składniki środowisko wykonawcze systemu Windows do eksportu, użyj opcji/WHOLEARCHIVE podczas łączenia tej biblioteki z innym składnikiem lub aplikacją.

Opcja/WHOLEARCHIVE została wprowadzona w programie Visual Studio 2015 Update 2.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać więcej informacji, [Zobacz C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości **wiersza polecenia** w obszarze **Właściwości konfiguracji**, **konsolidator**.

1. Dodaj opcję/WHOLEARCHIVE do pola tekstowego **Opcje dodatkowe** .

## <a name="see-also"></a>Zobacz też

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
