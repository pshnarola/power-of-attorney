<template>
  <div class="container-fluid">
    <div class="row mt-3">
      <div class="col">
        <form
          class="card card-body"
          novalidate
          autocomplete="off"
          @submit.prevent="downloadPDF()"
        >
          <input
            type="text"
            class="mb-3 form-control"
            v-model="lawFirm"
            placeholder="Law firm"
          />
          <input
            type="text"
            class="mb-3 form-control"
            v-model="representative"
            placeholder="Representative"
          />
          <textarea
            class="mb-3 form-control"
            id="exampleFormControlTextarea1"
            rows="2"
            placeholder="Address"
            v-model="address"
          ></textarea>
          <input
            type="text"
            class="mb-3 form-control"
            v-model="trademark"
            placeholder="Trademark"
          />
          <input
            type="text"
            class="mb-3 form-control"
            v-model="applicationNumber"
            placeholder="Application Number"
          />
          <div class="mb-3 datepicker-wrapper">
            <datepicker v-model="formDate" placeholder="Select date" />
          </div>
          <input
            type="text"
            class="mb-3 form-control"
            v-model="company"
            placeholder="Company"
          />
          <input
            type="text"
            class="mb-3 form-control"
            v-model="signatory"
            placeholder="Signatory"
          />
          <input
            type="text"
            class="mb-3 form-control"
            v-model="position"
            placeholder="Position"
          />
          <div class="col">
            <button type="submit" class="btn btn-info float-end" id="btn-pdf">
              Print
            </button>
          </div>
        </form>
      </div>
      <div class="col-8">
        <div id="content" class="card card-body p-0">
          <div id="pdf">
            <div class="container logo w-100">
              <img
                src="../public/trademark.png"
                class="float-end"
                width="300"
                alt="trademark-logo"
              />
            </div>
            <div class="container d-flex flex-column align-items-center mt-3">
              <h2 class="mb-0">Vollmacht</h2>
              <p>(Power of Attorney)</p>

              <div class="row w-100">
                <div class="col d-flex flex-column info">
                  <strong>Advocaatenkantoor</strong>
                  <strong>Jurimark</strong>
                  <strong>Mr. drs Bas M Pels</strong>
                  <strong>Thus 20-12</strong>
                  <strong>6537 LW Nijmegen</strong>
                  <span style="color:#212529" class="mt-3"
                    >wird hiermit in Sachen</span
                  >
                </div>
                <div class="col d-flex flex-column info">
                  <div class="right-address d-flex flex-column info">
                    <strong>Law Offices of</strong>
                    <strong>{{ lawFirm }}</strong>
                    <strong>{{ representative }}</strong>
                    <strong class="mb-2" style="white-space: pre-line;">{{
                      address
                    }}</strong>
                  </div>
                  <em class="text-muted text-bold"
                    >Is hereby appointed in the matter of
                  </em>
                </div>
              </div>
              <hr class="w-100" />
              <h4 class="mb-0">
                <strong>
                  European Union Trademark Application
                  <span class="font-inherit">{{ trademark }} </span>
                  {{ applicationNumber ? "“" + applicationNumber + "”" : "" }}
                </strong>
              </h4>
              <hr class="w-100" />

              <!-- description -->
              <div class="row">
                <div class="col">
                  <p class="">
                    Vertretungsvollmacht erteilt für das Anmelde- und
                    Schutzbewilligungsverfahren, für das erteilte bzw.
                    eingetragene Schutzrecht sowie für das Einspruchs- ,
                    Nichtigkeits-, Zwangslizenz- oder Löschungsverfahren vor dem
                    Amt der Europäischen Union für Geistiges Eigentum, dem
                    Bundespatentgericht und dem Bundesgerichtshof. Die Vollmacht
                    schließt auch das Verfahren nach dem Vertrag über die
                    internationale Zusammenarbeit auf dem Gebiet des
                    Patentwesens (PCT) und dem Vertrag über die
                    Gemeinschaftsmarke ein.
                  </p>
                  <p>
                    Der Bevollmächtigte ist berechtigt, Untervollmachten zu
                    erteilen.
                  </p>
                  <p>
                    Aufgrund dieser Vollmacht ist er insbesondere zu folgenden
                    Rechtsgeschäften und Verfügungen ermächtigt: Alle
                    Mitteilungen, Bescheide und Beschlüsse des Patent- und
                    Markenamtes und der Gerichte in Empfang zu nehmen,
                    Rechtsmittel oder Rechtsbehelfe einzulegen und
                    zurückzunehmen, Vergleiche abzuschließen, auf die Anmeldung
                    oder das Schutzrecht ganz oder teilweise zu verzichten, die
                    Beschränkung des Patentes zu beantragen, eine
                    Lizenzbereitschaftserklärung abzugeben oder einen von einem
                    Gegner erhobenen Anspruch anzuerkennen, in Markensachen
                    Widerspruch gegen die Löschung der Marken oder Aberkennung
                    des Schutzes der Marke und gegen die Eintragung anderer
                    Marken sowie gegen die Schutzbewilligung für andere
                    IR-Marken zu erheben und die Löschung bzw. Schutzentziehung
                    anderer Marken und für andere IR-Marken zu beantragen,
                    gestellte Anträge zurückzunehmen, Zahlungen für den
                    Auftraggeber in Empfang zu nehmen, Strafanträge zu stellen.
                  </p>
                  <p>
                    (Nur bei ausländischen Vollmachtgebern:) Durch diese
                    Vollmacht ist der Rechtsanwalt zum Vertreter gemäß § 25
                    Patentgesetz, § 28 Gebrauchsmustergesetz, § 96 Markengesetz
                    und § 16 Geschmacksmustergesetz bestellt.
                  </p>
                  <p>
                    Erfüllungsort für alle Ansprüche aus dem der Vollmacht
                    zugrunde liegenden Rechtsverhältnis und Gerichtsstand ist
                    der Ort der Kanzlei des Rechtsanwalts.
                  </p>
                </div>
                <div class="col">
                  <p class="">
                    <strong>
                      <em>
                        to act for us/me in proceedings concerning applications,
                        registrations, granted or registered industrial or
                        intellectual property rights, and in proceedings
                        concerning opposition, nullity, compulsory license,
                        rectification, revocation or cancellation in the
                        European Union Intellectual Property Office (EUIPO),
                        before the Federal Patent Court and before the Federal
                        Court of Justice. This authorization includes also the
                        procedure under the Patent Cooperation Treaty (PCT) and
                        the community trademarks.
                      </em>
                    </strong>
                  </p>
                  <p>
                    <strong>
                      <em>
                        The authorized agent is authorized to grant powers of
                        substitution.
                      </em>
                    </strong>
                  </p>
                  <p>
                    <strong>
                      <em>
                        By virtue of this authorization, he is especially
                        empowered to carry out the following legal transactions
                        and disposals: to receive all communications, official
                        actions and decisions of the Patent and Trademark Office
                        and the courts; to lodge or withdraw legal measures or
                        legal remedies; to conclude agreements; to fully or
                        partially disclaim the application or the property
                        right; to apply for the restriction of a patent; to
                        deliver a declaration of readiness to license. or to
                        acknowledge a claim raised by an opposing party; in
                        matters of the trade marks to contest an application for
                        the cancellation or revocation of an entry in the
                        Register in respect of a trade mark, to enter opposition
                        against the registration of other trademarks including
                        internationally registered marks, and to apply for the
                        cancellation or revocation of an entry in the Register
                        in respect of other trademarks including internationally
                        registered marks; to withdraw applications; to receive
                        payments on behalf of the client(s); and to demand
                        penalties.
                      </em>
                    </strong>
                  </p>
                  <p>
                    <strong>
                      <em>
                        (For foreign clients only:) By this authorization, the
                        Attorney is appointed as representative in accordance
                        with the following German laws: § 25 of Patent Law, § 28
                        of the Utility Model Law. § 96 of the Trade Mark Law and
                        § 16 of the Register Designs Act.
                      </em>
                    </strong>
                  </p>
                  <p>
                    <strong>
                      <em>
                        Place of settlement and the court for all claims arising
                        out of the legal relationship existing by virtue of the
                        Power of Attorney are at the location where the office
                        of the Attorney is situated.
                      </em>
                    </strong>
                  </p>
                </div>

                <div class="col-12">
                  <p class="d-flex flex-column mt-3 mb-5">
                    <span>{{ date }}</span>
                    <span>{{ company }}</span>
                  </p>
                  <p>{{ signatory && signatory + "," }} {{ position }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { jsPDF } from "jspdf";
import moment from "moment";
import Datepicker from "vue3-datepicker";
export default {
  components: {
    Datepicker,
  },
  data() {
    return {
      lawFirm: "",
      representative: "",
      address: "",
      trademark: "",
      applicationNumber: "",
      formDate: "",
      company: "",
      signatory: "",
      position: "",
    };
  },
  computed: {
    date() {
      return this.formDate === ""
        ? ""
        : moment(this.formDate).format("MMM DD, YYYY");
    },
  },
  methods: {
    downloadPDF() {
      if (
        this.lawFirm &&
        this.representative &&
        this.address &&
        this.trademark &&
        this.applicationNumber &&
        this.formDate &&
        this.company &&
        this.signatory &&
        this.position
      ) {
        const content = window.document.querySelector("#pdf");
        var doc = new jsPDF("p", "px", [
          content.offsetWidth,
          content.offsetHeight,
        ]);
        let that = this;
        doc.html(content, {
          callback: function(doc) {
            doc.save(`trademark_${that.trademark}.pdf`);
          },
        });
      } else {
        alert("Please fill all the details.");
      }
    },
  },
};
</script>

<style scopped>
@import "./app.css";
</style>
