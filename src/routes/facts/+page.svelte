<script>
    import { fly } from 'svelte/transition';
    import { onMount } from 'svelte';
    let facts = [
    "Potatoes are the world's fourth largest food crop.",
    "Potatoes originated in the Andes Mountains of South America.",
    "Potatoes were first domesticated between 8000 and 5000 BC.",
    "There are over 4,000 varieties of potatoes worldwide.",
    "Potatoes are a good source of vitamin C and potassium.",
    "The potato is 80% water and 20% solid.",
    "Potato plants produce white, pink, red, blue, or purple flowers.",
    "China is the world's largest producer of potatoes.",
    "Potatoes were introduced to Europe in the 16th century.",
    "The Inca Indians in Peru were the first to cultivate potatoes.",
    "Potatoes were the first vegetable to be grown in space.",
    "The potato is a tuber, which is an enlarged underground stem.",
    "Potatoes belong to the nightshade family, Solanaceae.",
    "Potatoes can be used to make vodka and other spirits.",
    "Potato chips were invented in Saratoga Springs, New York, in 1853.",
    "Mashed potatoes are a popular dish worldwide.",
    "The world's largest potato weighed 18 pounds and 4 ounces.",
    "Potatoes can be stored for months in a cool, dark place.",
    "Potatoes are naturally gluten-free.",
    "Sweet potatoes are not actually potatoes; they're from a different plant family.",
    "Potato skins are rich in fiber and nutrients.",
    "The term 'couch potato' was coined in 1976.",
    "Potatoes are used in biodegradable products.",
    "Potatoes can generate electricity in science experiments.",
    "Potatoes are the leading vegetable crop in the United States.",
    "French fries are believed to have been invented in Belgium.",
    "The Great Famine in Ireland was caused by potato blight.",
    "Potatoes are used to make gnocchi in Italian cuisine.",
    "Potatoes can be purple, red, yellow, or white inside.",
    "Potato starch is used as a thickener in foods.",
    "The word 'potato' comes from the Spanish word 'patata'.",
    "Potatoes are a staple food for many cultures.",
    "Potato leaves and stems are poisonous if ingested.",
    "Potatoes produce small, toxic fruits that resemble green tomatoes.",
    "The annual Potato Festival is celebrated in Peru.",
    "Potatoes can be grown from 'eyes' on the tuber.",
    "Potato plants can grow up to 2 feet tall.",
    "Potatoes are related to tomatoes and eggplants.",
    "Potatoes have been grown on the International Space Station.",
    "Potatoes were once banned in France due to superstition.",
    "The 'La Bonnotte' potato is the most expensive in the world.",
    "Potatoes can help reduce blood pressure due to their potassium content.",
    "Potatoes have more potassium than bananas.",
    "Potato blossoms were a fashion statement in Marie Antoinette's court.",
    "The potato's scientific name is Solanum tuberosum.",
    "Potatoes can be used to remove rust.",
    "Potatoes can help soothe burns and itchy skin.",
    "Potatoes can absorb excess salt in soups and stews.",
    "Potatoes can be used to polish silverware.",
    "Potato batteries can power small electronic devices.",
    "Potatoes are grown in over 125 countries.",
    "Potatoes are used in animal feed.",
    "In Germany, potatoes were initially fed to livestock, not humans.",
    "Potatoes contain antioxidants that promote health.",
    "Potatoes have been used to make stamps and ink.",
    "Potatoes can help improve digestive health.",
    "Potatoes were the first food photographed by a camera.",
    "Potatoes can be used in eco-friendly packaging.",
    "Potatoes are prescribed in some cultures for healing.",
    "Potato juice is used as a folk remedy for ulcers.",
    "Potato festivals are popular in potato-growing regions.",
    "Potatoes can help with weight gain when needed.",
    "Potatoes are cholesterol-free.",
    "Potatoes can be cooked in numerous ways.",
    "The largest potato-producing state in the U.S. is Idaho.",
    "Potatoes were once used as a measure of time in Ireland.",
    "Potatoes can help clean up polluted soil.",
    "Potatoes are used in traditional medicine in some cultures.",
    "Potatoes can suffer from over 100 different diseases.",
    "Potatoes are propagated vegetatively.",
    "Potatoes can be stored as frozen, dehydrated, or canned products.",
    "Potatoes can grow in poor soil conditions.",
    "Potatoes have been genetically engineered for pest resistance.",
    "Potatoes are part of crop rotation systems.",
    "The potato blight is caused by Phytophthora infestans.",
    "Potato starch is used in the textile industry.",
    "Potatoes can be used to produce ethanol fuel.",
    "Potatoes have been to the Moon aboard Apollo missions.",
    "Potato peels can be used to clean tarnished silver.",
    "Potatoes contain vitamin B6.",
    "Potatoes can be grown in containers.",
    "Potatoes can reduce inflammation.",
    "The blue potato is native to the Andes.",
    "Potatoes can help stabilize blood sugar levels.",
    "Potatoes are used in cosmetics for skin lightening.",
    "Potatoes have a low calorie density.",
    "Potatoes can improve heart health.",
    "Potatoes were once used to treat rheumatism.",
    "Potato flakes are used in instant mashed potatoes.",
    "Potatoes can help purify water in some treatments.",
    "Potatoes have been featured in art by artists like Van Gogh.",
    "Potatoes are celebrated on National Potato Day.",
    "Potatoes can be affected by pests like the Colorado potato beetle.",
    "Potato flowers were worn by royalty.",
    "Potatoes have played a role in wars as a food source.",
    "Potatoes can help strengthen bones.",
    "Potatoes can be grown year-round in some climates.",
    "Potatoes can absorb and reflect radio waves.",
    "Potatoes are used in plant research and breeding.",
    "Potatoes can suffer from frost damage.",
    "Potatoes have inspired numerous recipes worldwide.",
    "Potatoes can be dehydrated into potato flour.",
    "Potatoes contain compounds that may prevent cancer.",
    "Potatoes can be a part of gluten-free diets.",
    "Potatoes have been used in biodegradable plastics.",
    "Potatoes can be fertilized with compost and manure.",
    "Potatoes are a symbol of sustenance and comfort.",
    "Potatoes can be grown from true seeds, but it's uncommon.",
    "Potatoes can help improve soil health.",
    "Potatoes in space experiments help study plant growth.",
    "Potatoes have a versatile culinary profile.",
    "Potatoes can be used to make bread and pastries.",
    "Potatoes are involved in cultural traditions and folklore.",
    "Potatoes can be made into alcoholic beverages like poitín.",
    "Potatoes are an important global food security crop."
]

    let current_fact = $state("")
    
    function newFact() {
        current_fact = facts[Math.floor(Math.random() * facts.length)]
    }

    onMount(() => {
        newFact();
    });
</script>
<div class="flex flex-auto justify-center items-center p-4">
<button onclick={newFact} class="bg-cyan-400 rounded-3xl p-2">New Fact</button>
</div>


<h2 class="text-center text-3xl p-5" transition:fly >{current_fact}</h2>

<p class="text-center font-mono text-gray-400 text-md">facts are AI generated an may be inncorrect</p>
