<template>
  <div class="min-h-screen flex flex-col items-center justify-center bg-gray-100 text-gray-900 p-6">
    <h1 class="text-2xl font-bold mb-4">Gerar PDF em Blob</h1>

    <!-- Input para título do PDF -->
    <input 
      v-model="titulo"
      type="text"
      placeholder="Digite o título do PDF"
      class="px-3 py-2 border rounded w-80 mb-4"
    />

    <button 
      @click="gerarPdf"
      class="px-4 py-2 bg-blue-600 text-white rounded-lg shadow hover:bg-blue-700"
    >
      Gerar PDF e Abrir em Popup
    </button>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { jsPDF } from "jspdf";

const titulo = ref("Documento Profissional");

function gerarPdf() {
  const doc = new jsPDF({ unit: "mm", format: "a4" });

  // **Título centralizado**
  doc.setFont("helvetica", "bold");
  doc.setFontSize(18);
  doc.text(titulo.value, 105, 20, { align: "center" });

  // **Configurações de fonte para o conteúdo**
  doc.setFont("helvetica", "normal");
  doc.setFontSize(12);

  const conteudo = `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus in finibus diam, sed consectetur quam. Pellentesque vel porttitor ligula, sit amet volutpat lorem. Mauris bibendum, ipsum vitae semper venenatis, dui turpis euismod magna, ut hendrerit libero nibh eget risus. Duis in dictum ex. Donec porta elit felis, a vehicula nunc tincidunt sit amet. Ut sed bibendum velit, ac tempor purus. Nulla ac interdum est, ut sollicitudin sem. Maecenas pulvinar metus id mi fringilla, quis elementum lectus semper. Aliquam a cursus diam, sit amet sagittis sem. Nunc a orci ut risus tincidunt efficitur. Nunc id risus diam. Suspendisse et velit fermentum, fermentum lorem at, dictum nibh. Suspendisse non magna sit amet sapien varius eleifend.

Phasellus sodales dolor nec viverra accumsan. Curabitur bibendum erat vel massa tempus iaculis. Etiam vel ultricies magna. Nulla laoreet libero et auctor ornare. Aliquam erat volutpat. Donec mollis diam consequat augue imperdiet, nec tincidunt nisi egestas. Interdum et malesuada fames ac ante ipsum primis in faucibus. Morbi ut feugiat est. Suspendisse elementum fermentum ex, eget tempus magna pulvinar a.

Cras eu egestas erat. Nam pellentesque ante sit amet tincidunt dignissim. Maecenas tristique odio non elementum sollicitudin. Phasellus scelerisque justo eget lectus vulputate imperdiet. Morbi molestie aliquam ex, nec maximus lorem hendrerit elementum. Aliquam sit amet iaculis risus. Etiam lobortis eu risus eget condimentum. Aenean consectetur sed diam tincidunt ultricies. Aenean convallis commodo pharetra. Pellentesque quis gravida diam. Interdum et malesuada fames ac ante ipsum primis in faucibus. Vivamus ultricies porttitor elementum. Sed dignissim convallis vulputate.

Phasellus aliquet commodo nisi eu ullamcorper. Proin bibendum sapien tempor, faucibus nisi at, ornare ipsum. Curabitur ut efficitur erat. Pellentesque lobortis sapien sit amet mauris interdum placerat id nec neque. Nullam semper nisl in dui aliquet, non placerat mi ullamcorper. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Nunc id velit in erat mollis imperdiet viverra sit amet metus. Etiam eleifend maximus ligula, sit amet sollicitudin arcu tincidunt in. Donec sagittis libero vel tellus rutrum, vel aliquet ex congue. Maecenas cursus nunc neque, vel egestas lectus consequat eu. Fusce id maximus nulla, in sagittis orci.

Mauris vel mattis enim. Maecenas in risus magna. Vestibulum luctus rhoncus massa. Nam est diam, consectetur eget ligula sollicitudin, fermentum pellentesque quam. Nulla tellus lorem, consequat ut ultrices ac, rhoncus ac metus. Vestibulum sollicitudin felis vel ex mollis ultrices. Donec pharetra varius purus eget blandit. Sed iaculis eget ante vel condimentum. Nullam magna sem, lobortis at erat ac, iaculis pharetra nibh. Duis in mi mollis, condimentum odio quis, sollicitudin dolor.

Sed faucibus tortor tincidunt lorem tincidunt, finibus scelerisque nisl maximus. Etiam at libero in nisl dictum rutrum nec non velit. Donec sollicitudin est felis, in venenatis risus ultricies at. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia curae; Suspendisse eget quam feugiat sapien luctus mollis. Nullam at lectus at massa consectetur lobortis eu in nisi. Sed feugiat ante sit amet quam vehicula, quis vehicula enim suscipit. Curabitur molestie, urna feugiat rhoncus venenatis, leo lacus dictum dolor, vitae tempor lorem diam eu lorem. Ut erat orci, iaculis eu quam at, gravida ultricies massa. Praesent hendrerit arcu et justo efficitur ultricies. Aenean mattis auctor lectus quis sollicitudin. Vestibulum sodales erat nec ex fringilla, sed rutrum lorem convallis. Sed ultricies imperdiet eleifend.

Donec ut ultricies risus. Proin at tellus non arcu commodo porta vitae non felis. Etiam et ipsum purus. Pellentesque sagittis lorem vitae magna elementum bibendum. Nullam tincidunt justo id justo viverra, sed bibendum libero rhoncus. Pellentesque nunc ex, porttitor non tellus nec, eleifend rhoncus mauris. Integer interdum semper purus, nec euismod sem laoreet a. Sed pulvinar posuere ultricies. Nam varius felis odio, ultrices venenatis neque lacinia quis. Ut eget elit iaculis, tempus tortor sed, sodales arcu. Etiam id est lacinia, hendrerit purus sed, lacinia urna. Proin at dui sit amet turpis pulvinar volutpat a vel neque. Phasellus placerat augue ut libero faucibus bibendum.

Curabitur non leo id sem viverra suscipit quis in augue. Sed ut libero at ex tincidunt mattis. Cras fermentum quam a purus suscipit porta. Mauris eget magna venenatis, consequat ligula et, sagittis felis. Donec in est pellentesque, convallis quam eu, lacinia arcu. Maecenas est est, consectetur ac augue vitae, porttitor laoreet odio. Quisque rutrum ipsum urna, ut volutpat quam eleifend a. In quam velit, interdum in bibendum id, vulputate vitae nunc. Aliquam ultrices lacinia ipsum quis blandit. Maecenas porta, nunc in consequat vehicula, sem diam laoreet neque, sed scelerisque mi magna vel mi. Suspendisse potenti.

Ut ac nulla turpis. Aliquam diam urna, euismod quis felis tempor, malesuada rhoncus tellus. Aliquam eu eros lectus. Aliquam sit amet ipsum et tortor eleifend consequat. Phasellus pharetra ex massa, vitae elementum arcu fringilla ut. Sed faucibus tellus vel velit iaculis, iaculis iaculis lorem efficitur. Morbi aliquam felis eu augue lobortis, a porta magna sodales. Sed finibus velit elementum neque commodo ultrices. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Sed quam justo, molestie et purus in, fringilla tempor arcu.

Integer ullamcorper risus vel metus dapibus sagittis. Mauris tincidunt vulputate accumsan. Nullam ut ante non lectus consequat tincidunt ut quis felis. Vestibulum sed suscipit erat. Ut et quam nec felis vulputate egestas id in lectus. Sed hendrerit consectetur purus bibendum mattis. Vivamus condimentum at elit ac rutrum. Nulla aliquet ac odio eu rhoncus. Lorem ipsum dolor sit amet, consectetur adipiscing elit. In eu neque vitae nunc placerat molestie.

Maecenas et ligula et urna porttitor tincidunt at ultricies nisl. Phasellus quis consectetur nunc, a viverra metus. Integer sollicitudin orci pulvinar augue scelerisque fermentum. Etiam aliquam, magna nec euismod tempor, augue quam ornare nulla, a consectetur enim nisi et magna. Nunc finibus luctus erat et varius. Duis eu odio eget nunc rutrum porta nec ac lorem. Integer euismod consectetur mattis. In enim nulla, posuere sed rutrum quis, tempus id justo. Fusce ipsum quam, vulputate quis aliquet vel, consequat nec eros. Suspendisse sit amet odio varius nulla pharetra rhoncus.

Nunc in lorem ac arcu rhoncus laoreet eu vel neque. Cras sapien nibh, pulvinar consectetur tincidunt ut, ultrices vitae erat. Sed placerat augue libero. Pellentesque tincidunt, elit suscipit vestibulum commodo, nisi quam hendrerit mauris, id tincidunt orci augue in odio. Suspendisse egestas at sapien venenatis ultrices. Nulla nulla sem, lacinia sed tempor ac, egestas a orci. Donec sit amet imperdiet velit. Quisque et volutpat tellus. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin porta ac elit sed bibendum. Nam quis orci arcu. Suspendisse dictum non dolor et imperdiet. Sed porta iaculis maximus. Vestibulum maximus auctor odio ut imperdiet. Integer ut bibendum risus, ac vestibulum neque. Etiam et faucibus erat, ac convallis nunc.

Pellentesque feugiat rutrum libero, non euismod nunc vehicula eu. Integer porta libero a tempor luctus. Interdum et malesuada fames ac ante ipsum primis in faucibus. Proin non tincidunt nunc, sit amet venenatis nulla. Phasellus viverra, massa nec tincidunt lacinia, elit ex varius sapien, at finibus libero nisi vel tortor. Praesent ac rutrum orci. Pellentesque pellentesque congue nisi nec egestas. Nam rutrum accumsan sodales.

Nullam quis finibus nunc, quis tincidunt est. Morbi eget interdum quam. Pellentesque at dapibus dui. Fusce vestibulum tincidunt quam a tristique. Sed dignissim elit eu est tempus varius. Nullam rutrum accumsan arcu at tempor. Maecenas at lorem eu arcu auctor feugiat. Phasellus consequat velit congue velit varius, quis euismod ipsum sollicitudin. Quisque in vestibulum felis, ut sollicitudin eros. Proin ultricies lacus mauris, quis euismod lorem scelerisque eget. Ut quis dapibus libero. Maecenas at ultricies nisl, nec placerat est. Praesent nec massa sit amet eros molestie laoreet. Vestibulum in risus dignissim, porta turpis ac, porta sem. Proin nec ullamcorper magna, sed hendrerit diam. Vestibulum dapibus sagittis massa, in dignissim erat dapibus ut.

Mauris vitae orci pellentesque, euismod risus vel, sodales nisl. Suspendisse potenti. Vivamus quis enim placerat nunc vulputate tristique. Sed magna justo, viverra vitae eros eu, vehicula congue sem. Vestibulum sed gravida enim. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Fusce tempor dolor facilisis volutpat imperdiet.

Cras erat libero, lobortis quis ullamcorper eget, tristique ut urna. Suspendisse fringilla, ante vel porta tincidunt, felis tortor gravida elit, et laoreet felis urna vitae metus. Quisque sagittis suscipit quam non vestibulum. Nullam diam sapien, tempor eu bibendum at, elementum at est. Fusce ac dolor a arcu dapibus rutrum vel sed ex. Curabitur nunc magna, placerat quis mi quis, faucibus porta ligula. Donec venenatis, purus condimentum fringilla posuere, lectus elit facilisis dolor, at fringilla metus libero non felis. Praesent in dui sem. Pellentesque ultricies magna accumsan rutrum pharetra. Donec sed justo nisl. Interdum et malesuada fames ac ante ipsum primis in faucibus. Quisque commodo diam nibh, quis viverra eros ornare et. Curabitur at cursus ipsum, et facilisis massa. Cras vitae elit felis. Nulla facilisi.

Nam sit amet cursus nibh, vel mattis tortor. Fusce elementum, tortor et aliquet dignissim, dui mauris dapibus tortor, in pellentesque enim magna non est. Praesent eget bibendum massa. Cras porta leo ut magna molestie, ut auctor tellus commodo. Curabitur ut viverra felis. Morbi et lacus nec lorem ornare dictum. Sed aliquet sed tellus at rhoncus.

Donec id sapien nibh. Ut blandit aliquet fringilla. Vivamus pretium tristique vulputate. Vestibulum ac ex urna. Morbi vulputate magna sit amet metus viverra porta. Proin porttitor tellus nec nisi consequat, quis vehicula est maximus. Maecenas eget leo ac quam imperdiet viverra. Curabitur tempor sollicitudin eros, sed pharetra nisl porttitor tincidunt. Nullam erat nulla, gravida vel tempor eget, tempor sit amet ante. Aliquam erat volutpat. Aenean consectetur quam vitae sem egestas, et placerat ipsum suscipit. In dictum ornare orci quis facilisis. Mauris et lorem id orci eleifend tristique id eget sem. Nunc malesuada lobortis lectus vitae volutpat. Integer varius faucibus sem, non eleifend felis iaculis nec. Quisque libero nisl, eleifend et efficitur ut, posuere sed ipsum.

Praesent rutrum nibh at est mollis convallis. In velit justo, scelerisque sit amet ultricies id, accumsan nec augue. Donec varius sodales lacus quis lacinia. Duis sit amet ligula dui. Duis eu neque placerat, venenatis dui eget, varius lectus. Duis non consectetur dolor, et egestas metus. Pellentesque venenatis eros sed massa dictum, ut malesuada lectus mattis. Duis risus elit, convallis id fringilla eu, tristique nec massa. Pellentesque a sem ac ipsum ultrices sagittis. Vestibulum rutrum erat at eros posuere suscipit. Sed a aliquam nunc, sit amet tincidunt ante. Integer sed ipsum euismod, pretium metus nec, elementum dolor. Proin aliquam bibendum purus, et dapibus magna consequat vel. Praesent nec ex vel erat condimentum porttitor vel a enim. Donec interdum neque ante, pharetra elementum lectus auctor in. `;

  // **Margens e largura do texto**
  const marginLeft = 20;
  const marginTop = 35;
  const maxWidth = 170;

  doc.text(conteudo, marginLeft, marginTop, {
    maxWidth: maxWidth,
    align: "justify",
  });

  // **Gerar Blob e abrir em popup**
  const blob = doc.output("blob");
  const blobUrl = URL.createObjectURL(blob);
  window.open(blobUrl, "_blank", "width=800,height=600");
}
</script>
