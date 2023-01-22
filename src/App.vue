<template>
  <img src="https://upload.wikimedia.org/wikipedia/th/thumb/b/b7/MJU_LOGO.svg/1200px-MJU_LOGO.svg.png" alt="" style="display: block; height: 150px; margin-left: auto; margin-right: auto;">
  <h3>คำร้องขอโอนย้ายสาขาวิชา</h3>
  <p>เรื่อง ขอโอนย้ายสาขาวิชา</p>
  <form>
    <p>วันที่ <input type="date" name="" id="" required v-model="date"/></p>
    <div style="margin-left: 30px;">

      <div style="display: flex; gap: 15px; margin-top: 10px;">
        <div class="input-group">
          <span class="input-group-text">ชื่อ-นามสกุล</span>
          <input type="text" name="First name" placeholder="กรอกชื่อ" class="form-control" v-model="fName">
          <input type="text" name="Last name" placeholder="กรอกนามสกุล" class="form-control" v-model="lName">
        </div>
        <div class="input-group"  style="width: 50%;">
          <span class="input-group-text">รหัสนักศึกษา</span>
          <input type="text" name="stuID" placeholder="กรอกรหัสนักศึกษา" class="form-control" maxlength="10" required v-model="stuID">
        </div>
      </div>

      <div style="display: flex; gap: 15px;">
        <div class="input-group" style="width: 113%;">
          <span class="input-group-text">หมายเลขโทรศัพท์</span>
          <input type="text" name="Phone" placeholder="กรอกหมายเลขโทรศัพท์" class="form-control" required v-model="phone">
        </div>
        
        <div class="input-group"  style=" display: flex; flex-wrap: nowrap; width: fit-content;" >
          <span class="input-group-text">คณะ</span><select name="stuFac1" id="" v-model="stuFac1"> 
          <option value=""> กรุณาเลือกคณะ</option>
          <option value=""> คณะผลิตกรรมการเกษตร</option>
          <option value="">คณะวิศวกรรม</option>
          <option value="">คณะวิทยาศาสตร์</option>
          <option value="">วิทยาลัยบริหารศาสตร์</option>
          <option value="">คณะบริหารธุรกิจ</option>
          <option value="">คณะพัฒนาการท่องเที่ยว</option>
          <option value="">คณะเศรษฐศาสตร์</option> 
          </select>
        </div>
        <div class="input-group">
            <span class="input-group-text">สาขา</span>
            <input type="text" name="stuFac2" placeholder="กรอกสาขา" class="form-control" required v-model="stuFac2">
        </div>
      </div>
    <br>
    <hr size="8" width="100%">
    <br>
    
    <div style="display: flex; gap: 15px; justify-content: end;">
        <div class="input-group"  style=" display: flex; flex-wrap: nowrap;" >
          <span class="input-group-text">มีความประสงค์จะขอโอนย้ายไป คณะ</span><select name="wantFac1" id=""  v-model="stuWant1" required>
          <option value=""> กรุณาเลือกคณะ</option>
          <option value=""> คณะผลิตกรรมการเกษตร</option>
          <option value="">คณะวิศวกรรม</option>
          <option value="">คณะวิทยาศาสตร์</option>
          <option value="">วิทยาลัยบริหารศาสตร์</option>
          <option value="">คณะบริหารธุรกิจ</option>
          <option value="">คณะพัฒนาการท่องเที่ยว</option>
          <option value="">คณะเศรษฐศาสตร์</option> 
          </select>
        
          <span class="input-group-text">สาขา</span>
            <input type="text" name="wantFac2" placeholder="กรอกสาขา" class="form-control" required v-model="stuWant2">
        </div>
    </div>
    <div class="input-group">
      <span class="input-group-text">เนื่องจาก</span>
      <input name="bCouse" placeholder="" class="form-control" required v-model="abount">
      
    </div>  
    <div class="center"><button type="submit" class="btn btn-success" :disabled="stuWant2 <1" @click="add" >ส่งแบบฟอร์ม</button></div>
    <hr size="8" width="100%">
  </div>
  
</form>
<ul>
    <li v-for="data in myArray" :key="data.id">
    {{ data.id }}. {{ data.stuID }} {{ data.name }} จากสาขา {{ stuFac2 }} ต้องการย้ายไปสาขา {{ stuWant2 }} เนื่องจาก {{ data.abount }}   <button @click="delData(data.id)">delete</button>
    </li>
  </ul>

</template>



<style scoped>
h3 {
  text-align: center;
  margin-bottom: 2rem;
  margin-top: 1rem;
}
p {
  font-size: 17px;
  margin-bottom: 1rem;
}

.input-group{
  margin-bottom: 15px;
}
</style>

<script>

 export default {
  data(){
    return{
      date: "",
      fName: "",
      lName: "",
      stuID: "",
      phone: "",
      stuFac1: "",
      stuFac2: "",
      stuWant1: "",
      stuWant2: "",
      myArray:[]
    }
  },
  methods:{
    add(){
      this.myArray.push({
        id: this.myArray.length +1,
        stuID: this.stuID,
        name: this.fName +" "+this.lName,
        phone: this.phone,
        fac2: this.fac2,
        want2: this.stuWant2,
        abount: this.abount

      })
      this.date = '';
      this.fName = '';
      this.lName = '';
      this.stuFac1 = '';
      this.stuFac2 = '';
      this.stuID = '';
      this.phone = '';
      this.stuWant1 = '';
      this.stuWant2 = '';
      this.abount = '';

    },
    delData(dataID){
      this.myArray = this.myArray.filter(data => {
        return data.id !== dataID
      });
    }
  }
 }

</script>
