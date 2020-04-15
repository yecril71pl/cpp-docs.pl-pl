---
title: Klasa CPatht
ms.date: 03/27/2019
f1_keywords:
- CPathT
- ATLPATH/ATL::CPathT
- ATLPATH/ATL::CPathT::PCXSTR
- ATLPATH/ATL::CPathT::PXSTR
- ATLPATH/ATL::CPathT::XCHAR
- ATLPATH/ATL::CPathT::CPathT
- ATLPATH/ATL::CPathT::AddBackslash
- ATLPATH/ATL::CPathT::AddExtension
- ATLPATH/ATL::CPathT::Append
- ATLPATH/ATL::CPathT::BuildRoot
- ATLPATH/ATL::CPathT::Canonicalize
- ATLPATH/ATL::CPathT::Combine
- ATLPATH/ATL::CPathT::CommonPrefix
- ATLPATH/ATL::CPathT::CompactPath
- ATLPATH/ATL::CPathT::CompactPathEx
- ATLPATH/ATL::CPathT::FileExists
- ATLPATH/ATL::CPathT::FindExtension
- ATLPATH/ATL::CPathT::FindFileName
- ATLPATH/ATL::CPathT::GetDriveNumber
- ATLPATH/ATL::CPathT::GetExtension
- ATLPATH/ATL::CPathT::IsDirectory
- ATLPATH/ATL::CPathT::IsFileSpec
- ATLPATH/ATL::CPathT::IsPrefix
- ATLPATH/ATL::CPathT::IsRelative
- ATLPATH/ATL::CPathT::IsRoot
- ATLPATH/ATL::CPathT::IsSameRoot
- ATLPATH/ATL::CPathT::IsUNC
- ATLPATH/ATL::CPathT::IsUNCServer
- ATLPATH/ATL::CPathT::IsUNCServerShare
- ATLPATH/ATL::CPathT::MakePretty
- ATLPATH/ATL::CPathT::MatchSpec
- ATLPATH/ATL::CPathT::QuoteSpaces
- ATLPATH/ATL::CPathT::RelativePathTo
- ATLPATH/ATL::CPathT::RemoveArgs
- ATLPATH/ATL::CPathT::RemoveBackslash
- ATLPATH/ATL::CPathT::RemoveBlanks
- ATLPATH/ATL::CPathT::RemoveExtension
- ATLPATH/ATL::CPathT::RemoveFileSpec
- ATLPATH/ATL::CPathT::RenameExtension
- ATLPATH/ATL::CPathT::SkipRoot
- ATLPATH/ATL::CPathT::StripPath
- ATLPATH/ATL::CPathT::StripToRoot
- ATLPATH/ATL::CPathT::UnquoteSpaces
- ATLPATH/ATL::CPathT::m_strPath
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
ms.openlocfilehash: 13f46f549c7dd99852be0f322aef560cb454ed2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331471"
---
# <a name="cpatht-class"></a>Klasa CPatht

Ta klasa reprezentuje ścieżkę.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>Parametry

*Typ ciągu*<br/>
Klasa ciągu ATL/MFC do użycia dla ścieżki (zobacz [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)).

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CPathT::PCXSTR](#pcxstr)|Stały typ ciągu.|
|[CPathT::PXSTR](#pxstr)|Typ ciągu.|
|[CPathT::XCHAR](#xchar)|Typ znaku.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPathT::CPathT](#cpatht)|Konstruktor ścieżki.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPathT::AddBackslash](#addbackslash)|Wywołanie tej metody, aby dodać ukośnik odwrotny na końcu ciągu, aby utworzyć poprawną składnię ścieżki.|
|[CPathT::AddExtension](#addextension)|Wywołanie tej metody, aby dodać rozszerzenie pliku do ścieżki.|
|[CPathT::Dołącz](#append)|Wywołanie tej metody, aby dołączyć ciąg do bieżącej ścieżki.|
|[CPathT::BuildRoot](#buildroot)|Wywołanie tej metody, aby utworzyć ścieżkę główną z danego numeru dysku.|
|[CPathT::Canonicalize](#canonicalize)|Wywołanie tej metody, aby przekonwertować ścieżkę do postaci kanonicznej.|
|[CPathT::Kombajn](#combine)|Wywołanie tej metody, aby połączyć ciąg reprezentujący nazwę katalogu i ciąg reprezentujący nazwę ścieżki pliku w jednej ścieżce.|
|[CPathT::CommonPrefix](#commonprefix)|Wywołanie tej metody, aby ustalić, czy określona ścieżka dzieli wspólny prefiks z bieżącą ścieżką.|
|[CPathT::CompactPath](#compactpath)|Wywołanie tej metody, aby obciąć ścieżkę pliku, aby zmieścić się w obrębie danej szerokości piksela, zastępując składniki ścieżki elipsami.|
|[CPathT::CompactPathEx](#compactpathex)|Wywołanie tej metody, aby obciąć ścieżkę pliku, aby zmieścić się w określonej liczbie znaków, zastępując składniki ścieżki elipsami.|
|[CPathT::FileExists](#fileexists)|Wywołanie tej metody, aby sprawdzić, czy plik w tej nazwie ścieżki istnieje.|
|[CPathT::FindExtension](#findextension)|Wywołanie tej metody, aby znaleźć położenie rozszerzenia pliku w ścieżce.|
|[CPathT::FindFileName](#findfilename)|Wywołanie tej metody, aby znaleźć położenie nazwy pliku w ścieżce.|
|[CPathT::GetDriveNumber](#getdrivenumber)|Wywołanie tej metody, aby wyszukać ścieżkę dla litery dysku w zakresie od "A" do "Z" i zwrócić odpowiedni numer dysku.|
|[CPathT::GetExtension](#getextension)|Wywołanie tej metody, aby uzyskać rozszerzenie pliku ze ścieżki.|
|[CPathT::IsDirectory](#isdirectory)|Wywołanie tej metody, aby sprawdzić, czy ścieżka jest prawidłowy katalog.|
|[CPathT::IsFileSpec](#isfilespec)|Wywołanie tej metody, aby wyszukać ścieżkę dla dowolnych znaków\\wyznaczających ścieżkę (na przykład ':' lub ' ' ). Jeśli nie ma żadnych znaków rozdzielania ścieżki, ścieżka jest uważana za ścieżkę specyfikacji pliku.|
|[CPathT::IsPrefix](#isprefix)|Wywołanie tej metody, aby ustalić, czy ścieżka zawiera prawidłowy prefiks typu przekazywane przez *pszPrefix*.|
|[CPathT::IsRelative](#isrelative)|Wywołanie tej metody, aby ustalić, czy ścieżka jest względna.|
|[CPathT::IsRoot](#isroot)|Wywołanie tej metody, aby ustalić, czy ścieżka jest katalog główny.|
|[CPathT::IsSameRoot](#issameroot)|Wywołanie tej metody, aby ustalić, czy inna ścieżka ma wspólny składnik główny z bieżącą ścieżką.|
|[CPathT::IsuNC](#isunc)|Wywołanie tej metody, aby ustalić, czy ścieżka jest prawidłową ścieżką UNC (uniwersalna konwencja nazewnictwa) dla serwera i udziału.|
|[CPathT::IsUNCServer](#isuncserver)|Wywołanie tej metody, aby ustalić, czy ścieżka jest prawidłową ścieżką UNC (uniwersalna konwencja nazewnictwa) tylko dla serwera.|
|[CPathT::IsUNCServerShare](#isuncservershare)|Wywołanie tej metody, aby ustalić, czy ścieżka jest prawidłową \\ \ unc (uniwersalna konwencja nazewnictwa) współużytkować ścieżkę udziału,*udział* *serwera*\ .|
|[CPathT::MakePretty](#makepretty)|Wywołanie tej metody, aby przekonwertować ścieżkę do wszystkich małych znaków, aby nadać ścieżce spójny wygląd.|
|[CPathT::MatchSpec](#matchspec)|Wywołanie tej metody, aby wyszukać ścieżkę dla ciągu zawierającego typ dopasowania symboli wieloznacznych.|
|[CPathT::QuoteSpaces](#quotespaces)|Wywołanie tej metody, aby ująć ścieżkę w cudzysłów, jeśli zawiera ona spacje.|
|[CPathT::RelativePathTo](#relativepathto)|Wywołanie tej metody, aby utworzyć ścieżkę względną z jednego pliku lub folderu do innego.|
|[CPathT::RemoveArgs](#removeargs)|Wywołanie tej metody, aby usunąć wszystkie argumenty wiersza polecenia ze ścieżki.|
|[CPathT::RemoveBackslash](#removebackslash)|Wywołanie tej metody, aby usunąć końcowe ukośnik odwrotny ze ścieżki.|
|[CPathT::Usuńblaki](#removeblanks)|Wywołanie tej metody, aby usunąć wszystkie spacje wiodące i końcowe ze ścieżki.|
|[CPathT::UsuńWyświetlenie](#removeextension)|Wywołanie tej metody, aby usunąć rozszerzenie pliku ze ścieżki, jeśli istnieje.|
|[CPathT::RemoveFileSpec](#removefilespec)|Wywołanie tej metody, aby usunąć nazwę końcowego pliku i ukośnik odwrotny ze ścieżki, jeśli je ma.|
|[CPathT::Zmień nazwęWyświetlanie](#renameextension)|Wywołanie tej metody, aby zastąpić rozszerzenie nazwy pliku w ścieżce z nowym rozszerzeniem. Jeśli nazwa pliku nie zawiera rozszerzenia, rozszerzenie zostanie dołączone do końca ciągu.|
|[CPathT::SkipRoot](#skiproot)|Wywołanie tej metody, aby przeanalizować ścieżkę, ignorując literę dysku lub unc server/share path części.|
|[CPathT::StripPath](#strippath)|Wywołanie tej metody, aby usunąć część ścieżki w pełni kwalifikowany ścieżki i nazwy pliku.|
|[CPathT::StripToRoot](#striptoroot)|Wywołanie tej metody, aby usunąć wszystkie części ścieżki z wyjątkiem informacji głównych.|
|[CPathT::UnquoteSpaces](#unquotespaces)|Wywołanie tej metody, aby usunąć znaki cudzysłowu z początku i końca ścieżki.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPathT::operator const StringType &](#operator_const_stringtype_amp)|Ten operator umożliwia obiekt, który ma być traktowany jak ciąg.|
|[CPathT::operator CPathT::PCXSTR](#operator_cpatht__pcxstr)|Ten operator umożliwia obiekt, który ma być traktowany jak ciąg.|
|[CPathT::operator StringType &](#operator_stringtype_amp)|Ten operator umożliwia obiekt, który ma być traktowany jak ciąg.|
|[CPathT::operator +=](#operator_add_eq)|Ten operator dołącza ciąg do ścieżki.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPathT::m_strPath](#m_strpath)|Ścieżka.|

## <a name="remarks"></a>Uwagi

`CPath`, `CPathA`i `CPathW` są wystąpienia `CPathT` zdefiniowane w następujący sposób:

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlpath.h

## <a name="cpathtaddbackslash"></a><a name="addbackslash"></a>CPathT::AddBackslash

Wywołanie tej metody, aby dodać ukośnik odwrotny na końcu ciągu, aby utworzyć poprawną składnię ścieżki. Jeśli ścieżka ma już końcowe ukośnik odwrotny, nie zostanie dodane żadne ukośnik odwrotny.

```
void AddBackslash();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathAddBackSlash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).

## <a name="cpathtaddextension"></a><a name="addextension"></a>CPathT::AddExtension

Wywołanie tej metody, aby dodać rozszerzenie pliku do ścieżki.

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parametry

*pszRozwusz*<br/>
Rozszerzenie pliku do dodania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).

## <a name="cpathtappend"></a><a name="append"></a>CPathT::Dołącz

Wywołanie tej metody, aby dołączyć ciąg do bieżącej ścieżki.

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>Parametry

*pszWiększ*<br/>
Ciąg do dokład.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).

## <a name="cpathtbuildroot"></a><a name="buildroot"></a>CPathT::BuildRoot

Wywołanie tej metody, aby utworzyć ścieżkę główną z danego numeru dysku.

```
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>Parametry

*Idrive*<br/>
Numer dysku (0 to A:, 1 to B:i tak dalej).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).

## <a name="cpathtcanonicalize"></a><a name="canonicalize"></a>CPathT::Canonicalize

Wywołanie tej metody, aby przekonwertować ścieżkę do postaci kanonicznej.

```
void Canonicalize();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).

## <a name="cpathtcombine"></a><a name="combine"></a>CPathT::Kombajn

Wywołanie tej metody, aby połączyć ciąg reprezentujący nazwę katalogu i ciąg reprezentujący nazwę ścieżki pliku w jednej ścieżce.

```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>Parametry

*pszDir*<br/>
Ścieżka katalogu.

*pszFile*<br/>
Ścieżka do pliku.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).

## <a name="cpathtcommonprefix"></a><a name="commonprefix"></a>CPathT::CommonPrefix

Wywołanie tej metody, aby ustalić, czy określona ścieżka dzieli wspólny prefiks z bieżącą ścieżką.

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>Parametry

*psz.*<br/>
Ścieżka do porównania z bieżącą.

### <a name="return-value"></a>Wartość zwracana

Zwraca wspólny prefiks.

### <a name="remarks"></a>Uwagi

Prefiks jest jednym z tych\\\\typów: "C: ", ".", "..", ".. \\\\". Aby uzyskać więcej informacji, zobacz [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).

## <a name="cpathtcompactpath"></a><a name="compactpath"></a>CPathT::CompactPath

Wywołanie tej metody, aby obciąć ścieżkę pliku, aby zmieścić się w obrębie danej szerokości piksela, zastępując składniki ścieżki elipsami.

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>Parametry

*Hdc*<br/>
Kontekst urządzenia używany dla metryk czcionek.

*nWidth (ww.*<br/>
Szerokość w pikselach, do których ciąg zostanie zmuszony do dopasowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).

## <a name="cpathtcompactpathex"></a><a name="compactpathex"></a>CPathT::CompactPathEx

Wywołanie tej metody, aby obciąć ścieżkę pliku, aby zmieścić się w określonej liczbie znaków, zastępując składniki ścieżki elipsami.

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parametry

*nMaxChars*<br/>
Maksymalna liczba znaków, które mają być zawarte w nowym ciągu, w tym kończący znak NULL.

*Dwflags*<br/>
Zarezerwowany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).

## <a name="cpathtcpatht"></a><a name="cpatht"></a>CPathT::CPathT

Konstruktor.

```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```

### <a name="parameters"></a>Parametry

*PSZPath*<br/>
Wskaźnik do ciągu ścieżki.

*Ścieżka*<br/>
Ciąg ścieżki.

## <a name="cpathtfileexists"></a><a name="fileexists"></a>CPathT::FileExists

Wywołanie tej metody, aby sprawdzić, czy plik w tej nazwie ścieżki istnieje.

```
BOOL FileExists() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli plik istnieje, WARTOŚĆ FAŁSZU w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).

## <a name="cpathtfindextension"></a><a name="findextension"></a>CPathT::FindExtension

Wywołanie tej metody, aby znaleźć położenie rozszerzenia pliku w ścieżce.

```
int FindExtension() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca położenie "." poprzedzające rozszerzenie. Jeśli nie zostanie znalezione żadne rozszerzenie, zwraca wartość -1.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).

## <a name="cpathtfindfilename"></a><a name="findfilename"></a>CPathT::FindFileName

Wywołanie tej metody, aby znaleźć położenie nazwy pliku w ścieżce.

```
int FindFileName() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca położenie nazwy pliku. Jeśli nie zostanie znaleziona żadna nazwa pliku, zwraca wartość -1.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).

## <a name="cpathtgetdrivenumber"></a><a name="getdrivenumber"></a>CPathT::GetDriveNumber

Wywołanie tej metody, aby wyszukać ścieżkę dla litery dysku w zakresie od "A" do "Z" i zwrócić odpowiedni numer dysku.

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca numer dysku jako liczbę całkowitą od 0 do 25 (odpowiadającą "Od" do "Z"), jeśli ścieżka ma literę dysku lub -1 w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).

## <a name="cpathtgetextension"></a><a name="getextension"></a>CPathT::GetExtension

Wywołanie tej metody, aby uzyskać rozszerzenie pliku ze ścieżki.

```
StringType GetExtension() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca rozszerzenie pliku.

## <a name="cpathtisdirectory"></a><a name="isdirectory"></a>CPathT::IsDirectory

Wywołanie tej metody, aby sprawdzić, czy ścieżka jest prawidłowy katalog.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość niezerową (16), jeśli ścieżka jest katalogiem, w przeciwnym razie WARTOŚĆ FAŁSZ.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).

## <a name="cpathtisfilespec"></a><a name="isfilespec"></a>CPathT::IsFileSpec

Wywołanie tej metody, aby wyszukać ścieżkę dla dowolnych znaków\\wyznaczających ścieżkę (na przykład ':' lub ' ' ). Jeśli nie ma żadnych znaków rozdzielania ścieżki, ścieżka jest uważana za ścieżkę specyfikacji pliku.

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli w ścieżce nie ma znaków rozdzielających ścieżkę, lub wartość FAŁSZ, jeśli w ścieżce znajdują się znaki rozdzielające ścieżkę.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).

## <a name="cpathtisprefix"></a><a name="isprefix"></a>CPathT::IsPrefix

Wywołanie tej metody, aby ustalić, czy ścieżka zawiera prawidłowy prefiks typu przekazywane przez *pszPrefix*.

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>Parametry

*pszPrefix*<br/>
Prefiks, dla którego ma zostać wyszukany. Prefiks jest jednym z tych\\\\typów: "C: ", ".", "..", ".. \\\\".

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ścieżka zawiera prefiks lub FAŁSZ w inny sposób.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).

## <a name="cpathtisrelative"></a><a name="isrelative"></a>CPathT::IsRelative

Wywołanie tej metody, aby ustalić, czy ścieżka jest względna.

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ścieżka jest względna, lub WARTOŚĆ FAŁSZ, jeśli jest bezwzględna.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).

## <a name="cpathtisroot"></a><a name="isroot"></a>CPathT::IsRoot

Wywołanie tej metody, aby ustalić, czy ścieżka jest katalog główny.

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ścieżka jest katalogiem głównym lub FAŁSZ w inny sposób.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).

## <a name="cpathtissameroot"></a><a name="issameroot"></a>CPathT::IsSameRoot

Wywołanie tej metody, aby ustalić, czy inna ścieżka ma wspólny składnik główny z bieżącą ścieżką.

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>Parametry

*psz.*<br/>
Druga ścieżka.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli oba ciągi mają ten sam składnik główny lub FAŁSZ w inny sposób.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).

## <a name="cpathtisunc"></a><a name="isunc"></a>CPathT::IsuNC

Wywołanie tej metody, aby ustalić, czy ścieżka jest prawidłową ścieżką UNC (uniwersalna konwencja nazewnictwa) dla serwera i udziału.

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ścieżka jest prawidłową ścieżką UNC lub FAŁSZ w inny sposób.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).

## <a name="cpathtisuncserver"></a><a name="isuncserver"></a>CPathT::IsUNCServer

Wywołanie tej metody, aby ustalić, czy ścieżka jest prawidłową ścieżką UNC (uniwersalna konwencja nazewnictwa) tylko dla serwera.

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ciąg jest prawidłową ścieżką UNC tylko dla serwera (bez nazwy udziału) lub FAŁSZ w inny sposób.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).

## <a name="cpathtisuncservershare"></a><a name="isuncservershare"></a>CPathT::IsUNCServerShare

Wywołanie tej metody, aby ustalić, czy ścieżka jest prawidłową \\ \ unc (uniwersalna konwencja nazewnictwa) współużytkować ścieżkę udziału,*udział* *serwera*\ .

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli \\ \ ścieżka znajduje się w*udziale* *serwera*\ formularza lub FAŁD w inny sposób.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).

## <a name="cpathtm_strpath"></a><a name="m_strpath"></a>CPathT::m_strPath

Ścieżka.

```
StringType m_strPath;
```

### <a name="remarks"></a>Uwagi

`StringType`jest parametrem `CPathT`szablonu do .

## <a name="cpathtmakepretty"></a><a name="makepretty"></a>CPathT::MakePretty

Wywołanie tej metody, aby przekonwertować ścieżkę do wszystkich małych znaków, aby nadać ścieżce spójny wygląd.

```
BOOL MakePretty();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ścieżka została przekonwertowana lub FAŁSZ w inny sposób.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).

## <a name="cpathtmatchspec"></a><a name="matchspec"></a>CPathT::MatchSpec

Wywołanie tej metody, aby wyszukać ścieżkę dla ciągu zawierającego typ dopasowania symboli wieloznacznych.

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>Parametry

*pszSpec*<br/>
Wskaźnik do ciągu zakończonego wartością null z typem pliku, dla którego ma zostać wyszukany. Na przykład, aby sprawdzić, czy plik przy bieżącej ścieżce jest plikiem DOC, *pszSpec* powinien być ustawiony na "*.doc".

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ciąg jest zgodny lub FAŁSZ w inny sposób.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).

## <a name="cpathtoperator-"></a><a name="operator_add_eq"></a>CPathT::operator +=

Ten operator dołącza ciąg do ścieżki.

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>Parametry

*pszWiększ*<br/>
Ciąg do dokład.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowaną ścieżkę.

## <a name="cpathtoperator-const-stringtype-amp"></a><a name="operator_const_stringtype_amp"></a>CPathT::typ ciągu const operatora&amp;

Ten operator umożliwia obiekt, który ma być traktowany jak ciąg.

```
operator const StringType&() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg reprezentujący bieżącą ścieżkę zarządzaną przez ten obiekt.

## <a name="cpathtoperator-cpathtpcxstr"></a><a name="operator_cpatht__pcxstr"></a>CPathT::operator CPathT::PCXSTR

Ten operator umożliwia obiekt, który ma być traktowany jak ciąg.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg reprezentujący bieżącą ścieżkę zarządzaną przez ten obiekt.

## <a name="cpathtoperator-stringtype-amp"></a><a name="operator_stringtype_amp"></a>CPathT::operator StringType&amp;

Ten operator umożliwia obiekt, który ma być traktowany jak ciąg.

```
operator StringType&() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg reprezentujący bieżącą ścieżkę zarządzaną przez ten obiekt.

## <a name="cpathtpcxstr"></a><a name="pcxstr"></a>CPathT::PCXSTR

Stały typ ciągu.

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>Uwagi

`StringType`jest parametrem `CPathT`szablonu do .

## <a name="cpathtpxstr"></a><a name="pxstr"></a>CPathT::PXSTR

Typ ciągu.

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>Uwagi

`StringType`jest parametrem `CPathT`szablonu do .

## <a name="cpathtquotespaces"></a><a name="quotespaces"></a>CPathT::QuoteSpaces

Wywołanie tej metody, aby ująć ścieżkę w cudzysłów, jeśli zawiera ona spacje.

```
void QuoteSpaces();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).

## <a name="cpathtrelativepathto"></a><a name="relativepathto"></a>CPathT::RelativePathTo

Wywołanie tej metody, aby utworzyć ścieżkę względną z jednego pliku lub folderu do innego.

```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```

### <a name="parameters"></a>Parametry

*pszFrom*<br/>
Początek ścieżki względnej.

*dwAttrFrom*<br/>
Atrybuty pliku *pszFrom*. Jeśli ta wartość zawiera FILE_ATTRIBUTE_DIRECTORY, *pszFrom* zakłada się, że katalog; w przeciwnym razie *pszFrom* zakłada się, że jest to plik.

*pszTo*<br/>
Punkt końcowy ścieżki względnej.

*dwAttrTo*<br/>
Atrybuty pliku *pszTo*. Jeśli ta wartość zawiera FILE_ATTRIBUTE_DIRECTORY, *pszTo* zakłada się, że jest katalogiem; w przeciwnym razie *pszTo* zakłada się, że jest to plik.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).

## <a name="cpathtremoveargs"></a><a name="removeargs"></a>CPathT::RemoveArgs

Wywołanie tej metody, aby usunąć wszystkie argumenty wiersza polecenia ze ścieżki.

```
void RemoveArgs();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).

## <a name="cpathtremovebackslash"></a><a name="removebackslash"></a>CPathT::RemoveBackslash

Wywołanie tej metody, aby usunąć końcowe ukośnik odwrotny ze ścieżki.

```
void RemoveBackslash();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).

## <a name="cpathtremoveblanks"></a><a name="removeblanks"></a>CPathT::Usuńblaki

Wywołanie tej metody, aby usunąć wszystkie spacje wiodące i końcowe ze ścieżki.

```
void RemoveBlanks();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).

## <a name="cpathtremoveextension"></a><a name="removeextension"></a>CPathT::UsuńWyświetlenie

Wywołanie tej metody, aby usunąć rozszerzenie pliku ze ścieżki, jeśli istnieje.

```
void RemoveExtension();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).

## <a name="cpathtremovefilespec"></a><a name="removefilespec"></a>CPathT::RemoveFileSpec

Wywołanie tej metody, aby usunąć nazwę końcowego pliku i ukośnik odwrotny ze ścieżki, jeśli je ma.

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).

## <a name="cpathtrenameextension"></a><a name="renameextension"></a>CPathT::Zmień nazwęWyświetlanie

Wywołanie tej metody, aby zastąpić rozszerzenie nazwy pliku w ścieżce z nowym rozszerzeniem. Jeśli nazwa pliku nie zawiera rozszerzenia, rozszerzenie zostanie dołączone do końca ścieżki.

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parametry

*pszRozwusz*<br/>
Nowe rozszerzenie nazwy pliku, poprzedzone znakiem ".".

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).

## <a name="cpathtskiproot"></a><a name="skiproot"></a>CPathT::SkipRoot

Wywołanie tej metody, aby przeanalizować ścieżkę, ignorując literę dysku lub UNC (uniwersalna konwencja nazewnictwa) serwer/udział części ścieżki.

```
int SkipRoot() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca położenie początku ścieżki podrzędnej, która następuje po katalogu głównym (litera dysku lub serwer/udział UNC).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).

## <a name="cpathtstrippath"></a><a name="strippath"></a>CPathT::StripPath

Wywołanie tej metody, aby usunąć część ścieżki w pełni kwalifikowany ścieżki i nazwy pliku.

```
void StripPath();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).

## <a name="cpathtstriptoroot"></a><a name="striptoroot"></a>CPathT::StripToRoot

Wywołanie tej metody, aby usunąć wszystkie części ścieżki z wyjątkiem informacji głównych.

```
BOOL StripToRoot();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli w ścieżce znaleziono prawidłową literę dysku lub w inny sposób fałsz.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).

## <a name="cpathtunquotespaces"></a><a name="unquotespaces"></a>CPathT::UnquoteSpaces

Wywołanie tej metody, aby usunąć znaki cudzysłowu z początku i końca ścieżki.

```
void UnquoteSpaces();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).

## <a name="cpathtxchar"></a><a name="xchar"></a>CPathT::XCHAR

Typ znaku.

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>Uwagi

`StringType`jest parametrem `CPathT`szablonu do .

## <a name="see-also"></a>Zobacz też

[Klasy](../../atl/reference/atl-classes.md)<br/>
[CStringT, klasa](../../atl-mfc-shared/reference/cstringt-class.md)
