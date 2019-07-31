---
title: Word JavaScript API 要件セット1.2
description: WordApi 1.2 要件セットの詳細
ms.date: 07/17/2019
ms.prod: word
localization_priority: Normal
ms.openlocfilehash: c6244b7ce9ff7b5cbde68baad26e60a6326199d8
ms.sourcegitcommit: 6d9b4820a62a914c50cef13af8b80ce626034c26
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2019
ms.locfileid: "35804707"
---
# <a name="whats-new-in-word-javascript-api-12"></a><span data-ttu-id="eac5d-103">Word JavaScript API 1.2 の新機能</span><span class="sxs-lookup"><span data-stu-id="eac5d-103">What's new in Word JavaScript API 1.2</span></span>

<span data-ttu-id="eac5d-104">WordApi 1.2 インライン画像のサポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="eac5d-104">WordApi 1.2 added support for inline pictures.</span></span>

## <a name="api-list"></a><span data-ttu-id="eac5d-105">API リスト</span><span class="sxs-lookup"><span data-stu-id="eac5d-105">API list</span></span>

<span data-ttu-id="eac5d-106">次の表に、WordApi 1.2 要件セットの一部として追加される Api を示します。</span><span class="sxs-lookup"><span data-stu-id="eac5d-106">The following table lists the APIs added as part of the WordApi 1.2 requirement set.</span></span>

| <span data-ttu-id="eac5d-107">クラス</span><span class="sxs-lookup"><span data-stu-id="eac5d-107">Class</span></span> | <span data-ttu-id="eac5d-108">フィールド</span><span class="sxs-lookup"><span data-stu-id="eac5d-108">Fields</span></span> | <span data-ttu-id="eac5d-109">説明</span><span class="sxs-lookup"><span data-stu-id="eac5d-109">Description</span></span> |
|:---|:---|:---|
|[<span data-ttu-id="eac5d-110">Body</span><span class="sxs-lookup"><span data-stu-id="eac5d-110">Body</span></span>](/javascript/api/word/word.body)|[<span data-ttu-id="eac5d-111">insertInlinePictureFromBase64 (base64EncodedImage: string, insertLocation: Word InsertLocation)</span><span class="sxs-lookup"><span data-stu-id="eac5d-111">insertInlinePictureFromBase64(base64EncodedImage: string, insertLocation: Word.InsertLocation)</span></span>](/javascript/api/word/word.body#insertinlinepicturefrombase64-base64encodedimage--insertlocation-)|<span data-ttu-id="eac5d-112">画像を本文の指定された位置に挿入します。</span><span class="sxs-lookup"><span data-stu-id="eac5d-112">Inserts a picture into the body at the specified location.</span></span> <span data-ttu-id="eac5d-113">insertLocation の値には、'Start' または 'End' を指定できます。</span><span class="sxs-lookup"><span data-stu-id="eac5d-113">The insertLocation value can be 'Start' or 'End'.</span></span>|
|[<span data-ttu-id="eac5d-114">ContentControl</span><span class="sxs-lookup"><span data-stu-id="eac5d-114">ContentControl</span></span>](/javascript/api/word/word.contentcontrol)|[<span data-ttu-id="eac5d-115">insertInlinePictureFromBase64 (base64EncodedImage: string, insertLocation: Word InsertLocation)</span><span class="sxs-lookup"><span data-stu-id="eac5d-115">insertInlinePictureFromBase64(base64EncodedImage: string, insertLocation: Word.InsertLocation)</span></span>](/javascript/api/word/word.contentcontrol#insertinlinepicturefrombase64-base64encodedimage--insertlocation-)|<span data-ttu-id="eac5d-116">コンテンツ コントロール内の指定された位置にインライン画像を挿入します。</span><span class="sxs-lookup"><span data-stu-id="eac5d-116">Inserts an inline picture into the content control at the specified location.</span></span> <span data-ttu-id="eac5d-117">insertLocation 値には、'Replace'、'Start'、'End' のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="eac5d-117">The insertLocation value can be 'Replace', 'Start', or 'End'.</span></span>|
|[<span data-ttu-id="eac5d-118">InlinePicture</span><span class="sxs-lookup"><span data-stu-id="eac5d-118">InlinePicture</span></span>](/javascript/api/word/word.inlinepicture)|[<span data-ttu-id="eac5d-119">delete()</span><span class="sxs-lookup"><span data-stu-id="eac5d-119">delete()</span></span>](/javascript/api/word/word.inlinepicture#delete--)|<span data-ttu-id="eac5d-120">ドキュメントからインライン画像を削除します。</span><span class="sxs-lookup"><span data-stu-id="eac5d-120">Deletes the inline picture from the document.</span></span>|
||[<span data-ttu-id="eac5d-121">insertBreak (breakType: BreakType, Insertbreak: Word Insertbreak)</span><span class="sxs-lookup"><span data-stu-id="eac5d-121">insertBreak(breakType: Word.BreakType, insertLocation: Word.InsertLocation)</span></span>](/javascript/api/word/word.inlinepicture#insertbreak-breaktype--insertlocation-)|<span data-ttu-id="eac5d-122">メイン文書の指定した位置に、区切りを挿入します。</span><span class="sxs-lookup"><span data-stu-id="eac5d-122">Inserts a break at the specified location in the main document.</span></span> <span data-ttu-id="eac5d-123">有効な insertLocation の値は、'Before' または 'After' です。</span><span class="sxs-lookup"><span data-stu-id="eac5d-123">The insertLocation value can be 'Before' or 'After'.</span></span>|
||[<span data-ttu-id="eac5d-124">insertFileFromBase64 (base64File: string, insertLocation: Word InsertLocation)</span><span class="sxs-lookup"><span data-stu-id="eac5d-124">insertFileFromBase64(base64File: string, insertLocation: Word.InsertLocation)</span></span>](/javascript/api/word/word.inlinepicture#insertfilefrombase64-base64file--insertlocation-)|<span data-ttu-id="eac5d-125">指定した位置に文書を挿入します。</span><span class="sxs-lookup"><span data-stu-id="eac5d-125">Inserts a document at the specified location.</span></span> <span data-ttu-id="eac5d-126">有効な insertLocation の値は、'Before' または 'After' です。</span><span class="sxs-lookup"><span data-stu-id="eac5d-126">The insertLocation value can be 'Before' or 'After'.</span></span>|
||[<span data-ttu-id="eac5d-127">insertHtml (html: string, insertLocation: Word. InsertLocation)</span><span class="sxs-lookup"><span data-stu-id="eac5d-127">insertHtml(html: string, insertLocation: Word.InsertLocation)</span></span>](/javascript/api/word/word.inlinepicture#inserthtml-html--insertlocation-)|<span data-ttu-id="eac5d-128">指定した位置に HTML を挿入します。</span><span class="sxs-lookup"><span data-stu-id="eac5d-128">Inserts HTML at the specified location.</span></span> <span data-ttu-id="eac5d-129">有効な insertLocation の値は、'Before' または 'After' です。</span><span class="sxs-lookup"><span data-stu-id="eac5d-129">The insertLocation value can be 'Before' or 'After'.</span></span>|
||[<span data-ttu-id="eac5d-130">insertInlinePictureFromBase64 (base64EncodedImage: string, insertLocation: Word InsertLocation)</span><span class="sxs-lookup"><span data-stu-id="eac5d-130">insertInlinePictureFromBase64(base64EncodedImage: string, insertLocation: Word.InsertLocation)</span></span>](/javascript/api/word/word.inlinepicture#insertinlinepicturefrombase64-base64encodedimage--insertlocation-)|<span data-ttu-id="eac5d-131">指定された位置にインライン画像を挿入します。</span><span class="sxs-lookup"><span data-stu-id="eac5d-131">Inserts an inline picture at the specified location.</span></span> <span data-ttu-id="eac5d-132">InsertLocation の値には、' Replace '、' Before '、または ' After ' を指定できます。</span><span class="sxs-lookup"><span data-stu-id="eac5d-132">The insertLocation value can be 'Replace', 'Before', or 'After'.</span></span>|
||[<span data-ttu-id="eac5d-133">insertOoxml (ooxml: string, insertLocation: Word. InsertLocation)</span><span class="sxs-lookup"><span data-stu-id="eac5d-133">insertOoxml(ooxml: string, insertLocation: Word.InsertLocation)</span></span>](/javascript/api/word/word.inlinepicture#insertooxml-ooxml--insertlocation-)|<span data-ttu-id="eac5d-134">指定した位置に OOXML を挿入します。</span><span class="sxs-lookup"><span data-stu-id="eac5d-134">Inserts OOXML at the specified location.</span></span>  <span data-ttu-id="eac5d-135">有効な insertLocation の値は、'Before' または 'After' です。</span><span class="sxs-lookup"><span data-stu-id="eac5d-135">The insertLocation value can be 'Before' or 'After'.</span></span>|
||[<span data-ttu-id="eac5d-136">insertParagraph (paragraphText: string, Insertparagraph: Word. Insertparagraph)</span><span class="sxs-lookup"><span data-stu-id="eac5d-136">insertParagraph(paragraphText: string, insertLocation: Word.InsertLocation)</span></span>](/javascript/api/word/word.inlinepicture#insertparagraph-paragraphtext--insertlocation-)|<span data-ttu-id="eac5d-137">指定した位置に、段落を挿入します。</span><span class="sxs-lookup"><span data-stu-id="eac5d-137">Inserts a paragraph at the specified location.</span></span> <span data-ttu-id="eac5d-138">有効な insertLocation の値は、'Before' または 'After' です。</span><span class="sxs-lookup"><span data-stu-id="eac5d-138">The insertLocation value can be 'Before' or 'After'.</span></span>|
||[<span data-ttu-id="eac5d-139">insertText (text: string, insertLocation: Word. InsertLocation)</span><span class="sxs-lookup"><span data-stu-id="eac5d-139">insertText(text: string, insertLocation: Word.InsertLocation)</span></span>](/javascript/api/word/word.inlinepicture#inserttext-text--insertlocation-)|<span data-ttu-id="eac5d-140">指定した位置にテキストを挿入します。</span><span class="sxs-lookup"><span data-stu-id="eac5d-140">Inserts text at the specified location.</span></span> <span data-ttu-id="eac5d-141">insertLocation の値には、'Before' または 'After' を指定できます。</span><span class="sxs-lookup"><span data-stu-id="eac5d-141">The insertLocation value can be 'Before' or 'After'.</span></span>|
||[<span data-ttu-id="eac5d-142">段落</span><span class="sxs-lookup"><span data-stu-id="eac5d-142">paragraph</span></span>](/javascript/api/word/word.inlinepicture#paragraph)|<span data-ttu-id="eac5d-143">インライン イメージを含む親段落を取得します。</span><span class="sxs-lookup"><span data-stu-id="eac5d-143">Gets the parent paragraph that contains the inline image.</span></span> <span data-ttu-id="eac5d-144">読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="eac5d-144">Read-only.</span></span>|
||[<span data-ttu-id="eac5d-145">select (selectionMode?:. SelectionMode)</span><span class="sxs-lookup"><span data-stu-id="eac5d-145">select(selectionMode?: Word.SelectionMode)</span></span>](/javascript/api/word/word.inlinepicture#select-selectionmode-)|<span data-ttu-id="eac5d-146">インライン画像を選択します。</span><span class="sxs-lookup"><span data-stu-id="eac5d-146">Selects the inline picture.</span></span> <span data-ttu-id="eac5d-147">その結果、Word は選択範囲にスクロールされます。</span><span class="sxs-lookup"><span data-stu-id="eac5d-147">This causes Word to scroll to the selection.</span></span>|
|[<span data-ttu-id="eac5d-148">Range</span><span class="sxs-lookup"><span data-stu-id="eac5d-148">Range</span></span>](/javascript/api/word/word.range)|[<span data-ttu-id="eac5d-149">insertInlinePictureFromBase64 (base64EncodedImage: string, insertLocation: Word InsertLocation)</span><span class="sxs-lookup"><span data-stu-id="eac5d-149">insertInlinePictureFromBase64(base64EncodedImage: string, insertLocation: Word.InsertLocation)</span></span>](/javascript/api/word/word.range#insertinlinepicturefrombase64-base64encodedimage--insertlocation-)|<span data-ttu-id="eac5d-150">指定された位置に画像を挿入します。</span><span class="sxs-lookup"><span data-stu-id="eac5d-150">Inserts a picture at the specified location.</span></span> <span data-ttu-id="eac5d-151">InsertLocation の値には、' Replace '、' Start '、' End '、' Before '、または ' After ' を指定できます。</span><span class="sxs-lookup"><span data-stu-id="eac5d-151">The insertLocation value can be 'Replace', 'Start', 'End', 'Before', or 'After'.</span></span>|
||[<span data-ttu-id="eac5d-152">inlinePictures</span><span class="sxs-lookup"><span data-stu-id="eac5d-152">inlinePictures</span></span>](/javascript/api/word/word.range#inlinepictures)|<span data-ttu-id="eac5d-153">範囲に含まれるインライン画像オブジェクトのコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="eac5d-153">Gets the collection of inline picture objects in the range.</span></span> <span data-ttu-id="eac5d-154">読み取り専用。</span><span class="sxs-lookup"><span data-stu-id="eac5d-154">Read-only.</span></span>|

## <a name="see-also"></a><span data-ttu-id="eac5d-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="eac5d-155">See also</span></span>

- [<span data-ttu-id="eac5d-156">Word JavaScript API リファレンスドキュメント</span><span class="sxs-lookup"><span data-stu-id="eac5d-156">Word JavaScript API Reference Documentation</span></span>](/javascript/api/word)
- [<span data-ttu-id="eac5d-157">Word JavaScript API の要件セット</span><span class="sxs-lookup"><span data-stu-id="eac5d-157">Word JavaScript API requirement sets</span></span>](word-api-requirement-sets.md)