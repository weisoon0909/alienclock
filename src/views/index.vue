<template>
    <div>
        <h1>Alien Clock</h1>
        <div>
            <p>Current Alien Time: {{ alienTime.year }}-{{ alienTime.month }}-{{ alienTime.day }} {{ alienTime.hour
                }}:{{ alienTime.minute }}:{{ alienTime.second }}</p>
            <p>Current Earth Time: {{ currentEarthTime }}</p>
        </div>
        <div class="flex gap-x-5 mt-5">
            <div>
                <h3>Set Alien Time</h3>
                <div class="container">

                    <form class="grid gap-x-5 grid-cols-2">
                        <div class="mb-5">
                            <label for="large-input"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Year</label>
                            <input v-model="newAlienTime.year" placeholder="Year" type="number"
                                class="block w-full p-4 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-base focus:ring-blue-500 focus:border-blue-500">
                        </div>
                        <div class="mb-5">
                            <label for="large-input"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Month</label>
                            <input v-model="newAlienTime.month" placeholder="Month" type="number"
                                class="block w-full p-4 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-base focus:ring-blue-500 focus:border-blue-500">
                        </div>
                        <div class="mb-5">
                            <label for="large-input"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Day</label>
                            <input v-model="newAlienTime.day" placeholder="Day" type="number"
                                class="block w-full p-4 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-base focus:ring-blue-500 focus:border-blue-500">
                        </div>
                        <div class="mb-5">
                            <label for="large-input"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Hour</label>
                            <input v-model="newAlienTime.hour" placeholder="Hour" type="number"
                                class="block w-full p-4 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-base focus:ring-blue-500 focus:border-blue-500">
                        </div>
                        <div class="mb-5">
                            <label for="large-input"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Minute</label>
                            <input v-model="newAlienTime.minute" placeholder="Minute" type="number"
                                class="block w-full p-4 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-base focus:ring-blue-500 focus:border-blue-500">
                        </div>
                        <div class="mb-5">
                            <label for="large-input"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Second</label>
                            <input v-model="newAlienTime.second" placeholder="Second" type="number"
                                class="block w-full p-4 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-base focus:ring-blue-500 focus:border-blue-500">
                        </div>
                    </form>
                </div>
                <button class="text-white bg-blue-700 hover:bg-blue-800 rounded-lg text-sm px-5 py-2.5 text-center"
                    @click="setAlienTime">Set Alien Time</button>
            </div>
            <div class="border-l-2 pl-5">
                <h3>Set Alien Alarm Time</h3>
                <div class="container">

                    <form class="grid gap-x-5 grid-cols-2">
                        <div class="mb-5">
                            <label for="large-input"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Year</label>
                            <input v-model="alarmTime.year" placeholder="Year" type="number"
                                class="block w-full p-4 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-base focus:ring-blue-500 focus:border-blue-500">
                        </div>
                        <div class="mb-5">
                            <label for="large-input"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Month</label>
                            <input v-model="alarmTime.month" placeholder="Month" type="number"
                                class="block w-full p-4 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-base focus:ring-blue-500 focus:border-blue-500">
                        </div>
                        <div class="mb-5">
                            <label for="large-input"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Day</label>
                            <input v-model="alarmTime.day" placeholder="Day" type="number"
                                class="block w-full p-4 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-base focus:ring-blue-500 focus:border-blue-500">
                        </div>
                        <div class="mb-5">
                            <label for="large-input"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Hour</label>
                            <input v-model="alarmTime.hour" placeholder="Hour" type="number"
                                class="block w-full p-4 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-base focus:ring-blue-500 focus:border-blue-500">
                        </div>
                        <div class="mb-5">
                            <label for="large-input"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Minute</label>
                            <input v-model="alarmTime.minute" placeholder="Minute" type="number"
                                class="block w-full p-4 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-base focus:ring-blue-500 focus:border-blue-500">
                        </div>
                        <div class="mb-5">
                            <label for="large-input"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Second</label>
                            <input v-model="alarmTime.second" placeholder="Second" type="number"
                                class="block w-full p-4 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-base focus:ring-blue-500 focus:border-blue-500">
                        </div>
                    </form>
                </div>
                <button class="text-white bg-blue-700 hover:bg-blue-800 rounded-lg text-sm px-5 py-2.5 text-center"
                    @click="setAlarm">Set Alarm Time</button>

                    <p v-if="alarmSet">Alarm is Set at {{ alarmTime.year }}-{{ alarmTime.month }}-{{ alarmTime.day }} {{ alarmTime.hour
                }}:{{ alarmTime.minute }}:{{ alarmTime.second }}</p>
            </div>

        </div>


    </div>
</template>

<script>
export default {
    data() {
        return {
            alienTime: {
                year: 2804,
                month: 18,
                day: 31,
                hour: 2,
                minute: 2,
                second: 88
            },
            currentEarthTime: new Date(),
            newAlienTime: {
                year: 2804,
                month: 18,
                day: 31,
                hour: 2,
                minute: 2,
                second: 88
            },
            alarmTime: {
                year: 2804,
                month: 18,
                day: 31,
                hour: 2,
                minute: 2,
                second: 88
            },
            alarmTriggered: false,
            alarmSet: false
        };
    },
    mounted() {
        // update alien clock every 0.5 earth second
        setInterval(() => {
            this.updateAlienClock();
            this.checkAlarm();
        }, 500);
    },
    methods: {
        updateAlienClock() {
            // increment alien time by 1 second
            this.alienTime.second++;
            if (this.alienTime.second >= 90) {
                this.alienTime.second = 0;
                this.alienTime.minute++;
                if (this.alienTime.minute >= 90) {
                    this.alienTime.minute = 0;
                    this.alienTime.hour++;
                    if (this.alienTime.hour >= 36) {
                        this.alienTime.hour = 0;
                        this.alienTime.day++;
                        const daysInMonth = this.getDaysInMonth(this.alienTime.month);
                        if (this.alienTime.day > daysInMonth) {
                            this.alienTime.day = 1;
                            this.alienTime.month++;
                            if (this.alienTime.month > 18) {
                                this.alienTime.month = 1;
                                this.alienTime.year++;
                            }
                        }
                    }
                }
            }
            this.currentEarthTime = new Date(this.currentEarthTime.getTime() + 500); // update earth time
        },
        getDaysInMonth(month) {
            const daysInMonths = [44, 42, 48, 40, 48, 44, 40, 44, 42, 40, 40, 42, 44, 48, 42, 40, 44, 38];
            return daysInMonths[month - 1];
        },
        setAlienTime() {
            this.alienTime = { ...this.newAlienTime };
        },
        setAlarm() {
            this.alarmSet = true
            this.alarmTriggered = false;
        },
        checkAlarm() {
            if (
                this.alarmTime.year === this.alienTime.year &&
                this.alarmTime.month === this.alienTime.month &&
                this.alarmTime.day === this.alienTime.day &&
                this.alarmTime.hour === this.alienTime.hour &&
                this.alarmTime.minute === this.alienTime.minute &&
                this.alarmTime.second === this.alienTime.second
            ) {
                this.triggerAlarm();
            }
        },
        triggerAlarm() {
            this.alarmTriggered = true;
            alert('🚨 Alarm Triggered! 🚨');
        }
    }
};
</script>

<style>
.container {
    display: flex;
}
</style>