const KEY='jk_dungeon_v2'; const CFGKEY='jk_dungeon_config_v2';
const MODES={low:{name:'低学年',icon:'🌱',desc:'小学1〜2年生向け。ひらがな中心・計算と並びの謎',mult:1},middle:{name:'中学年',icon:'🗝️',desc:'小学3〜4年生向け。漢字・暗号・かけ算と文章の謎',mult:1.5},high:{name:'高学年',icon:'⚔️',desc:'小学5〜6年生向け。割合・論理・複雑な暗号',mult:2},master:{name:'それ以上',icon:'🃏',desc:'超高難度。16種類の複合暗号・論理問題と、4つの断片を集める裏迷宮。隠し部屋は特別条件付き',mult:3}};
const defaultCfg={questions:[],stories:{},modeSettings:{},rewards:[{id:'floor5',title:'5階のひみつ',trigger:'floor',target:'5',code:'',limit:'once',chance:100},{id:'room3',title:'森の隠し部屋',trigger:'room',target:'secret_3',code:'',limit:'once',chance:100}],message:'ジョーカーの影が、どこかでこちらを見ている……'};
function getCfg(){try{return {...defaultCfg,...JSON.parse(localStorage.getItem(CFGKEY)||'{}')}}catch{return structuredClone(defaultCfg)}}
function saveCfg(c){localStorage.setItem(CFGKEY,JSON.stringify(c))}
function escapeHtml(s){return String(s??'').replace(/[&<>"']/g,a=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[a]))}
function randInt(n){return Math.floor(Math.random()*n)}
function rng(seed){let x=(seed*1664525+1013904223)>>>0;return ()=>((x=(x*1664525+1013904223)>>>0)/4294967296)}
function currentDay(){return new Date().toISOString().slice(0,10)}
