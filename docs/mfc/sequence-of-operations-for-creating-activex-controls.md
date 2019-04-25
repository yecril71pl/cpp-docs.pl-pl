---
title: Sekwencja operacji przy tworzeniu kontrolek ActiveX
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
- sequence [MFC], for creating ActiveX controls
- OLE controls [MFC], MFC
- sequence [MFC]
ms.assetid: 7d868c53-a0af-4ef6-a89c-e1c03c583a53
ms.openlocfilehash: 020c044cc0b3b96df102a5ab6625c945f1033f67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308436"
---
# <a name="sequence-of-operations-for-creating-activex-controls"></a>Sekwencja operacji przy tworzeniu kontrolek ActiveX

W poniższej tabeli przedstawiono usługi roli i roli struktury w tworzeniu kontrolek ActiveX (dawniej formantów OLE).

### <a name="creating-activex-controls"></a>Tworzenie kontrolki ActiveX

|Zadanie|Możesz zrobić|Struktura jest|
|----------|------------|------------------------|
|Utwórz platforma kontrolki ActiveX.|Uruchom Kreator kontrolek ActiveX MFC do tworzenia kontrolki. Określ żądane opcje na stronach opcji. Opcje obejmują typ i nazwę formantu w projekcie, licencjonowanie, podklasy oraz metodę o polu.|Kreator kontrolek ActiveX MFC tworzy pliki kontrolki ActiveX z podstawowymi funkcjami, w tym pliki źródłowe dla aplikacji, kontrolki i stronę właściwości lub stron. Plik zasobów; plik projektu; i inne, wszystkie dostosowane do specyfikacji.|
|Zobacz, Kreator kontrolek ActiveX i kontrolki oferują bez dodawania linię własnym kodem.|Tworzenie formantu ActiveX i przetestować go za pomocą programu Internet Explorer lub [przykładowe TSTCON](../overview/visual-cpp-samples.md).|Uruchamianie kontroli ma możliwość można zmienić rozmiar i przenieść. Ma on także **o polu** metody (Jeśli wybrano), który może być wywoływany.|
|Implementuje metody i właściwości formantu.|Implementuje właściwości i metody specyficzne dla formantu, dodając funkcje Członkowskie udostępnia interfejs narażonych na danych formantu. Dodaj zmienne Członkowskie do przechowywania struktur danych i umożliwia wyzwolenie zdarzenia po określeniu procedury obsługi zdarzeń.|Struktura został już zdefiniowany mapy w celu obsługi zdarzeń, właściwości i metod, pozostawiając pozwala skupić się na implementacji właściwości i metod formantu. Domyślna strona właściwości jest widoczny, a podano domyślną metodę o polu.|
|Konstruowania strony właściwości lub strony formantu.|Edytory zasobów Visual C++ umożliwiają wizualne edytowanie interfejs strony właściwości formantu:<br /><br />— Tworzenie strony właściwości dodatkowych.<br />-Tworzenie i edytowanie map bitowych, ikon i kursorów.<br /><br /> Możesz także testować stron właściwości w edytorze okien dialogowych.|Domyślny plik zasobów tworzone przez Kreatora aplikacji MFC udostępnia wiele zasobów, których potrzebujesz. Visual C++ pozwala edytować istniejące zasoby i dodać nowe zasoby, łatwe i wizualnie.|
|Przetestuj zdarzenia, metod i właściwości formantu.|Ponownie skompiluj kontrolkę i użyć kontenera testu do testowania, czy inne programy obsługi działają poprawnie.|Można wywołać metody kontroli i modyfikowania jego właściwości, za pośrednictwem interfejsu strony właściwości lub kontener testu. Ponadto należy użyć kontenera testu do śledzenia zdarzeń wyzwalanych z formantu i powiadomienia odbierane przez kontener formantu.|

## <a name="see-also"></a>Zobacz także

[Opieranie się na strukturze](../mfc/building-on-the-framework.md)<br/>
[Sekwencja operacji przy tworzeniu aplikacji MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[Sekwencja operacji przy tworzeniu aplikacji OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[Sekwencja operacji przy tworzeniu aplikacji bazy danych](../mfc/sequence-of-operations-for-creating-database-applications.md)
