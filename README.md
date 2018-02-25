<h3> This is a library for indexing a document or extracting unique non stopwords tokens and getting their frequency </h3>

<h3> For indexing call the function IndexDocument and listen for the <u> finish </u> event when indexing completed and also you can access extracted token using the <u>tokens</u> property and it is a Map data structure</h3>

<code>

const HtmlIndexer =require('./htmlIndexer');
const indexer = new HtmlIndexer();

    indexer.IndexDocument("tests/test.html");
        indexer.on("indexFinished", () => {
            for (var key of indexer.tokens.keys()) {
                console.log(`Term : ${key}    Frequency : ${indexer.tokens.get(key)}`);
            }
        });
</code>


<h3> You can access generated tokens with using stream with <u>getOutPutStream</u> passing chunk size or number of tokens 

per chunk and the output is json based with format <b>{ term: 'test', freq: 1, isFirstChunk: true, isLastChunk: true } </b></h3>




<code>
            var stream =indexer.getOutPutStream(2);
            
            stream.on('data',(data)=>console.log(data));

</code>