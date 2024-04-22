# RAG

使用するLLMは、OpenAIのgpt-3.5-turboであり、Vector StoreにはFAISSを使用し、EmbeddingにはOpenAIEmbeddingsを使用しました。

実際に投げかける質問文は、「On which datasets does GPT-3 struggle?」です。 

1. 「pypdfを元にした」LangChainのラッパーを使用して、PDFを読み込み、Document objectを作成します。
2. Document objectを適切なチャンクサイズに分割します。
3. 「OpenAIEmbeddings と FAISS オブジェクトを作成します。作成したチャンクをベクトル化し、保存します。 
4. FAISS データベースから、関連の深い文章を「5件」抽出するretrieverを作成します。
5. 「ChatPromptTemplate クラスを用いて、上記5件の文章を参照して、質問への回答を返すようなプロンプトテンプレートを作成します。
6. ChatOpenAIクラスを使用して、「gpt-3.5-turbo に質問を行うことができる」modelを作成します。
7. chainを作成し、RAG機能を作成し、最後に質問を行います。

