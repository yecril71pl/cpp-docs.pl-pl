---
title: Obsługa zestawów znaków wielobajtowych (zestawy MBCS)
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- multibyte characters [C++]
- MBCS [C++]
ms.assetid: b498733c-a1e1-45e3-8f26-d6da3cb5f2dd
ms.openlocfilehash: 0b43168ec4331e99dea7e939b097674cc880804e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375765"
---
# <a name="support-for-multibyte-character-sets-mbcss"></a>Obsługa zestawów znaków wielobajtowych (zestawy MBCS)

Wielobajtowe zestawy znaków (MBCSs) to starsze podejście do potrzeby obsługi zestawów znaków, takich jak japoński i chiński, które nie mogą być reprezentowane w jednym bajcie. Jeśli robisz nowe rozwoju, należy użyć Unicode dla wszystkich ciągów tekstowych, z wyjątkiem być może ciągów systemowych, które nie są widoczne dla użytkowników końcowych. MBCS jest starszą technologią i nie jest zalecany do nowego rozwoju.

Najczęstszą implementacją MBCS są zestawy znaków dwu bajtowych (DBCSs). Visual C++ w ogóle, a MFC w szczególności jest w pełni włączone dla DBCS.

Aby uzyskać przykłady, zobacz pliki kodu źródłowego MFC.

W przypadku platform używanych na rynkach, których języki używają dużych zestawów znaków, najlepszą alternatywą dla Unicode jest MBCS. MFC obsługuje MBCS przy użyciu międzynarodowo różnych typów danych i funkcji wykonywania języka C. Należy zrobić to samo w kodzie.

W obszarze MBCS znaki są kodowane w 1 lub 2 bajtach. W znakach 2-bajtowych pierwszy lub bajt wiodący sygnalizuje, że zarówno on, jak i następujący bajt mają być interpretowane jako jeden znak. Pierwszy bajt pochodzi z zakresu kodów zarezerwowanych do użycia jako bajty potencjalnych potencjalnych. Zakresy bajtów mogą być bajtami potencjalnych potencjalnych potencjalnych klienty, zależy od używanej strony kodowej. Na przykład japońska strona kodowa 932 używa zakresu od 0x81 do 0x9F jako bajtów potencjalnych potencjalnych potencjalnych klient, ale koreańska strona kodowa 949 używa innego zakresu.

Rozważmy wszystkie poniższe elementy w programowaniu MBCS.

Znaki MBCS w środowisku znaków MBCS mogą pojawiać się w ciągach, takich jak nazwy plików i katalogów.

### <a name="editing-operations"></a>Operacje edycji

Operacje edycji w aplikacjach MBCS powinny działać na znakach, a nie bajtach. Przekaz nie powinien dzielić znaku, klawisz **strzałki** w prawo powinien przesuwać się w prawo o jeden znak itd. **Usuń** powinien usunąć znak; **Cofnij,** należy ponownie włożyć go.

### <a name="string-handling"></a>Obsługa ciągów

W aplikacji, która używa MBCS obsługi ciągów stwarza specjalne problemy. Znaki o obu szerokościach są mieszane w jednym ciągu; w związku z tym należy pamiętać, aby sprawdzić bajtów potencjalnych potencjalnych.

### <a name="run-time-library-support"></a>Obsługa biblioteki w czasie wykonywania

Biblioteka wykonywania języka C i MFC obsługują programowanie jedno bajtowe, MBCS i Unicode. Ciągi jedno bajtowe są `str` przetwarzane z rodziną funkcji w czasie wykonywania, ciągi MBCS są przetwarzane z odpowiednimi `_mbs` funkcjami, a ciągi Unicode są przetwarzane z odpowiednimi `wcs` funkcjami. Implementacje funkcji elementów członkowskich klasy MFC używają przenośnych funkcji w `str` czasie wykonywania, które mapują, w odpowiednich okolicznościach, do normalnej rodziny funkcji, funkcji MBCS lub funkcji Unicode, zgodnie z opisem w "MBCS/Unicode portability".

### <a name="mbcsunicode-portability"></a>Przenoszenie MBCS/Unicode

Za pomocą pliku nagłówka tchar.h można tworzyć aplikacje jedno bajtowe, MBCS i Unicode z tych samych źródeł. Tchar.h definiuje makra poprzedzone *_tcs* , które `str`mapują do , `_mbs`lub `wcs` funkcje, w stosownych przypadkach. Aby zbudować MBCS, `_MBCS`zdefiniuj symbol . Aby utworzyć unicode, `_UNICODE`zdefiniuj symbol . Domyślnie `_UNICODE` jest zdefiniowany dla aplikacji MFC. Aby uzyskać więcej informacji, zobacz [Mapowania tekstu ogólnego w tchar.h](../text/generic-text-mappings-in-tchar-h.md).

> [!NOTE]
> Zachowanie jest niezdefiniowane, `_UNICODE` `_MBCS`jeśli zdefiniujesz zarówno i .

Pliki nagłówkowe Mbctype.h i Mbstring.h definiują funkcje i makra specyficzne dla MBCS, które w niektórych przypadkach mogą być potrzebne. Na przykład `_ismbblead` informuje, czy określony bajt w ciągu jest bajtem wiodącym.

Aby uzyskać możliwość przenoszenia międzynarodowego, zakoduj program za pomocą zestawów znaków [Unicode](../text/support-for-unicode.md) lub wielobajtowych (MBCS).

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Włączanie MBC w programie](../text/international-enabling.md)

- [Włączanie zarówno Unicode, jak i MBCS w moim programie](../text/internationalization-strategies.md)

- [Tworzenie umięsionego programu za pomocą mbcs](../text/mbcs-programming-tips.md)

- [Zobacz podsumowanie programowania MBCS](../text/mbcs-programming-tips.md)

- [Dowiedz się więcej o mapowaniach tekstu ogólnego w celu przenoszenia szerokości bajtów](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Zobacz też

[Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)<br/>
[Obsługa MBCS w programie Visual C++](../text/mbcs-support-in-visual-cpp.md)
