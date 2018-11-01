---
title: / WHOLEARCHIVE (Dołącz wszystkie pliki obiektów biblioteki)
ms.date: 11/04/2016
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
ms.openlocfilehash: 26bd720a2ecd07bccb1317e1540cb071e7027078
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494227"
---
# <a name="wholearchive-include-all-library-object-files"></a>/ WHOLEARCHIVE (Dołącz wszystkie pliki obiektów biblioteki)

Wymuś na konsolidatorze załączenie wszystkie pliki obiektów biblioteki statycznej w połączony plik wykonywalny.

## <a name="syntax"></a>Składnia

> / WHOLEARCHIVE [:*biblioteki*]

## <a name="remarks"></a>Uwagi

Opcja /WHOLEARCHIVE wymusza konsolidator, aby uwzględnić każdy plik obiektu, z poziomu określonej biblioteki statycznej, lub jeśli biblioteka nie jest określony, wszystkie biblioteki statyczne, określony do łącza polecenia z. Aby określić opcję /WHOLEARCHIVE wiele bibliotek, służy więcej niż jednego przełącznika /WHOLEARCHIVE w wierszu polecenia konsolidatora. Domyślnie konsolidator zawiera pliki obiektów w danych wyjściowych w połączonych, tylko wtedy, gdy ich Eksportuj symbole przywoływany przez inne pliki obiektów w pliku wykonywalnym. Opcja /WHOLEARCHIVE sprawia, że konsolidator traktowanie wszystkich plików obiektu archiwizowane w bibliotece statycznej, tak, jakby zostały określone osobno w wierszu polecenia konsolidatora.

Opcja /WHOLEARCHIVE można ponownie wyeksportować wszystkie symbole z biblioteki statycznej. Dzięki temu można upewnić się, że wszystkie biblioteki kodu, zasoby i metadane są uwzględniane podczas tworzenia składnika z więcej niż jedna biblioteka statyczne. Jeśli zostanie wyświetlone ostrzeżenie LNK4264 podczas tworzenia biblioteki statycznej, który zawiera składniki środowiska wykonawczego Windows eksportu, należy użyć opcji /WHOLEARCHIVE podczas konsolidacji tej biblioteki do innej aplikacji lub składnika.

Opcja /WHOLEARCHIVE została wprowadzona w Visual Studio 2015 Update 2.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **wiersza polecenia** strony właściwości w obszarze **właściwości konfiguracji**, **konsolidatora**.

1. Dodaj opcję /WHOLEARCHIVE **dodatkowe opcje** pola tekstowego.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)